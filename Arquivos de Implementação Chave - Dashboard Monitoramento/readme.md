// ============================================================================
// ARQUIVO 1: apps/web/src/app/dashboard/monitoring/page.tsx
// Dashboard de Monitoramento Real-Time
// ============================================================================

'use client';

import { useEffect, useState } from 'react';
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card';
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs';
import { Alert, AlertDescription } from '@/components/ui/alert';
import { Badge } from '@/components/ui/badge';
import { Activity, Battery, Sun, Zap, AlertTriangle, TrendingUp } from 'lucide-react';

// Components
import GenerationChart from './components/GenerationChart';
import InverterStatus from './components/InverterStatus';
import BESSStatus from './components/BESSStatus';
import WeatherWidget from './components/WeatherWidget';
import AlertsPanel from './components/AlertsPanel';

// Hooks
import { useRealtimeData } from './hooks/useRealtimeData';
import { useWebSocket } from '@/hooks/useWebSocket';

// Types
import type { MonitoringData, SystemAlert } from '@/types/monitoring';

export default function MonitoringPage() {
  const { data, isLoading, error } = useRealtimeData();
  const { lastMessage, connectionStatus } = useWebSocket('ws://api.logiq.com/monitoring');
  
  const [systemAlerts, setSystemAlerts] = useState<SystemAlert[]>([]);

  useEffect(() => {
    if (lastMessage) {
      const parsedData = JSON.parse(lastMessage) as MonitoringData;
      // Update alerts if any anomalies detected
      if (parsedData.alerts) {
        setSystemAlerts(prev => [...parsedData.alerts, ...prev].slice(0, 10));
      }
    }
  }, [lastMessage]);

  if (isLoading) {
    return <div className="flex h-screen items-center justify-center">Carregando...</div>;
  }

  if (error) {
    return (
      <Alert variant="destructive">
        <AlertTriangle className="h-4 w-4" />
        <AlertDescription>Erro ao carregar dados: {error.message}</AlertDescription>
      </Alert>
    );
  }

  const { generation, inverters, bess, weather, performance } = data || {};

  return (
    <div className="space-y-6 p-6">
      {/* Header */}
      <div className="flex items-center justify-between">
        <div>
          <h1 className="text-3xl font-bold tracking-tight">Monitoramento Solar CD01</h1>
          <p className="text-muted-foreground">
            Sistema fotovoltaico 7,425 MWp + BESS 5 MWh
          </p>
        </div>
        <div className="flex items-center gap-2">
          <Badge variant={connectionStatus === 'connected' ? 'success' : 'destructive'}>
            {connectionStatus === 'connected' ? 'Online' : 'Offline'}
          </Badge>
          <span className="text-sm text-muted-foreground">
            Atualizado: {new Date().toLocaleTimeString('pt-BR')}
          </span>
        </div>
      </div>

      {/* KPI Cards */}
      <div className="grid gap-4 md:grid-cols-2 lg:grid-cols-4">
        <Card>
          <CardHeader className="flex flex-row items-center justify-between space-y-0 pb-2">
            <CardTitle className="text-sm font-medium">Geração Atual</CardTitle>
            <Sun className="h-4 w-4 text-yellow-500" />
          </CardHeader>
          <CardContent>
            <div className="text-2xl font-bold">
              {generation?.currentPower.toFixed(2)} MW
            </div>
            <p className="text-xs text-muted-foreground">
              {((generation?.currentPower / 7.425) * 100).toFixed(1)}% da capacidade
            </p>
          </CardContent>
        </Card>

        <Card>
          <CardHeader className="flex flex-row items-center justify-between space-y-0 pb-2">
            <CardTitle className="text-sm font-medium">Energia Hoje</CardTitle>
            <Zap className="h-4 w-4 text-blue-500" />
          </CardHeader>
          <CardContent>
            <div className="text-2xl font-bold">
              {generation?.dailyEnergy.toFixed(0)} MWh
            </div>
            <p className="text-xs text-muted-foreground">
              Meta: 32 MWh/dia
            </p>
          </CardContent>
        </Card>

        <Card>
          <CardHeader className="flex flex-row items-center justify-between space-y-0 pb-2">
            <CardTitle className="text-sm font-medium">BESS SOC</CardTitle>
            <Battery className="h-4 w-4 text-green-500" />
          </CardHeader>
          <CardContent>
            <div className="text-2xl font-bold">
              {bess?.stateOfCharge}%
            </div>
            <p className="text-xs text-muted-foreground">
              {bess?.currentPower > 0 ? 'Descarregando' : 'Carregando'} ({Math.abs(bess?.currentPower || 0).toFixed(1)} MW)
            </p>
          </CardContent>
        </Card>

        <Card>
          <CardHeader className="flex flex-row items-center justify-between space-y-0 pb-2">
            <CardTitle className="text-sm font-medium">Performance Ratio</CardTitle>
            <TrendingUp className="h-4 w-4 text-purple-500" />
          </CardHeader>
          <CardContent>
            <div className="text-2xl font-bold">
              {performance?.performanceRatio.toFixed(1)}%
            </div>
            <p className="text-xs text-muted-foreground">
              Meta: {'>'} 85%
            </p>
          </CardContent>
        </Card>
      </div>

      {/* Main Content Tabs */}
      <Tabs defaultValue="overview" className="space-y-4">
        <TabsList>
          <TabsTrigger value="overview">Visão Geral</TabsTrigger>
          <TabsTrigger value="inverters">Inversores</TabsTrigger>
          <TabsTrigger value="bess">BESS</TabsTrigger>
          <TabsTrigger value="alerts">Alertas</TabsTrigger>
        </TabsList>

        <TabsContent value="overview" className="space-y-4">
          <div className="grid gap-4 md:grid-cols-2 lg:grid-cols-7">
            <Card className="col-span-4">
              <CardHeader>
                <CardTitle>Geração em Tempo Real</CardTitle>
                <CardDescription>Últimas 24 horas</CardDescription>
              </CardHeader>
              <CardContent className="pl-2">
                <GenerationChart data={generation?.historical24h || []} />
              </CardContent>
            </Card>
            <Card className="col-span-3">
              <CardHeader>
                <CardTitle>Condições Climáticas</CardTitle>
                <CardDescription>Estação meteorológica local</CardDescription>
              </CardHeader>
              <CardContent>
                <WeatherWidget data={weather} />
              </CardContent>
            </Card>
          </div>
        </TabsContent>

        <TabsContent value="inverters" className="space-y-4">
          <InverterStatus inverters={inverters || []} />
        </TabsContent>

        <TabsContent value="bess" className="space-y-4">
          <BESSStatus bess={bess} />
        </TabsContent>

        <TabsContent value="alerts" className="space-y-4">
          <AlertsPanel alerts={systemAlerts} />
        </TabsContent>
      </Tabs>
    </div>
  );
}


// ============================================================================
// ARQUIVO 2: apps/api/src/modules/monitoring/monitoring.service.ts
// Service de Monitoramento (Backend)
// ============================================================================

import { Injectable, Logger } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';
import { Cron, CronExpression } from '@nestjs/schedule';

// Entities
import { Generation } from './entities/generation.entity';
import { Inverter } from './entities/inverter.entity';
import { BESS } from './entities/bess.entity';

// Services
import { ModbusService } from '../integrations/scada/modbus.service';
import { AlertsService } from '../alerts/alerts.service';
import { WeatherService } from '../integrations/weather/weather-api.service';

// DTOs
import { RealtimeDataDto } from './dto/realtime-data.dto';

@Injectable()
export class MonitoringService {
  private readonly logger = new Logger(MonitoringService.name);

  constructor(
    @InjectRepository(Generation)
    private generationRepo: Repository<Generation>,
    @InjectRepository(Inverter)
    private inverterRepo: Repository<Inverter>,
    @InjectRepository(BESS)
    private bessRepo: Repository<BESS>,
    private modbusService: ModbusService,
    private alertsService: AlertsService,
    private weatherService: WeatherService,
  ) {}

  /**
   * Coleta dados em tempo real via Modbus (SCADA)
   * Executado a cada 5 segundos
   */
  @Cron(CronExpression.EVERY_5_SECONDS)
  async collectRealtimeData(): Promise<RealtimeDataDto> {
    try {
      // 1. Coletar dados inversores (50 inversores via Modbus TCP)
      const invertersData = await Promise.all(
        Array.from({ length: 50 }, (_, i) => 
          this.modbusService.readInverter(i + 1)
        )
      );

      // 2. Coletar dados BESS
      const bessData = await this.modbusService.readBESS();

      // 3. Calcular totais
      const totalPower = invertersData.reduce((sum, inv) => sum + inv.activePower, 0) / 1000; // kW -> MW
      const dailyEnergy = invertersData.reduce((sum, inv) => sum + inv.dailyEnergy, 0) / 1000; // kWh -> MWh

      // 4. Coletar dados meteorológicos
      const weather = await this.weatherService.getCurrentConditions();

      // 5. Detectar anomalias
      const anomalies = await this.detectAnomalies(invertersData, bessData);
      
      if (anomalies.length > 0) {
        await this.alertsService.createAlerts(anomalies);
      }

      // 6. Salvar histórico (TimescaleDB otimizado)
      await this.saveHistorical({
        timestamp: new Date(),
        totalPower,
        dailyEnergy,
        invertersOnline: invertersData.filter(i => i.status === 'online').length,
        bessSOC: bessData.stateOfCharge,
        bessPower: bessData.activePower,
        irradiance: weather.irradiance,
        temperature: weather.temperature,
      });

      // 7. Retornar dados formatados
      return {
        generation: {
          currentPower: totalPower,
          dailyEnergy,
          monthlyEnergy: await this.getMonthlyEnergy(),
          historical24h: await this.getHistorical24h(),
        },
        inverters: invertersData.map(inv => ({
          id: inv.id,
          status: inv.status,
          activePower: inv.activePower,
          efficiency: inv.efficiency,
          temperature: inv.temperature,
          dcVoltage: inv.dcVoltage,
          dcCurrent: inv.dcCurrent,
        })),
        bess: {
          stateOfCharge: bessData.stateOfCharge,
          currentPower: bessData.activePower / 1000, // kW -> MW
          temperature: bessData.temperature,
          cycleCount: bessData.cycleCount,
          health: bessData.health,
        },
        weather: {
          irradiance: weather.irradiance,
          temperature: weather.temperature,
          humidity: weather.humidity,
          windSpeed: weather.windSpeed,
        },
        performance: {
          performanceRatio: await this.calculatePR(),
          capacityFactor: await this.calculateCF(),
          availability: await this.calculateAvailability(),
        },
        alerts: anomalies,
      };
    } catch (error) {
      this.logger.error(`Erro coletando dados: ${error.message}`, error.stack);
      throw error;
    }
  }

  /**
   * Detecta anomalias usando regras + ML
   */
  private async detectAnomalies(inverters: any[], bess: any): Promise<any[]> {
    const anomalies = [];

    // Regra 1: Inversor com potência muito baixa vs irradiância
    inverters.forEach((inv, idx) => {
      const expectedPower = inv.dcPower * 0.98; // 98% eficiência esperada
      if (inv.activePower < expectedPower * 0.7 && inv.status === 'online') {
        anomalies.push({
          type: 'underperformance',
          severity: 'medium',
          component: `Inverter ${idx + 1}`,
          message: `Potência ${inv.activePower}kW abaixo do esperado (${expectedPower.toFixed(0)}kW)`,
          recommendation: 'Verificar sombreamento ou falha módulos',
        });
      }
    });

    // Regra 2: BESS com temperatura elevada
    if (bess.temperature > 45) {
      anomalies.push({
        type: 'temperature_high',
        severity: bess.temperature > 55 ? 'high' : 'medium',
        component: 'BESS',
        message: `Temperatura ${bess.temperature}°C acima do limite (45°C)`,
        recommendation: 'Verificar sistema de refrigeração',
      });
    }

    // Regra 3: BESS com muitos ciclos (degradação)
    if (bess.cycleCount > 3000) {
      anomalies.push({
        type: 'battery_degradation',
        severity: 'low',
        component: 'BESS',
        message: `${bess.cycleCount} ciclos completos. Degradação esperada: ${((bess.cycleCount / 5000) * 20).toFixed(1)}%`,
        recommendation: 'Planejar substituição células em 2 anos',
      });
    }

    // Regra 4: Performance Ratio baixo
    const pr = await this.calculatePR();
    if (pr < 80) {
      anomalies.push({
        type: 'low_performance',
        severity: 'high',
        component: 'Sistema',
        message: `Performance Ratio ${pr.toFixed(1)}% abaixo de 85%`,
        recommendation: 'Limpeza painéis urgente ou verificar sombreamento',
      });
    }

    return anomalies;
  }

  /**
   * Calcula Performance Ratio (PR)
   * PR = Energia Real / Energia Teórica × 100%
   */
  private async calculatePR(): Promise<number> {
    const today = new Date();
    today.setHours(0, 0, 0, 0);

    const data = await this.generationRepo
      .createQueryBuilder('g')
      .where('g.timestamp >= :today', { today })
      .getMany();

    const realEnergy = data.reduce((sum, d) => sum + d.dailyEnergy, 0); // MWh
    const irradiance = data.reduce((sum, d) => sum + d.irradiance, 0) / data.length; // W/m² médio
    
    // Energia teórica = Potência × Irradiância × PSH / 1000
    const psh = irradiance * data.length / (1000 * 60); // Peak Sun Hours
    const theoreticalEnergy = 7.425 * psh; // 7.425 MWp × PSH

    return (realEnergy / theoreticalEnergy) * 100;
  }

  /**
   * Calcula Capacity Factor (CF)
   * CF = (Energia Mensal / Potência × 730h) × 100%
   */
  private async calculateCF(): Promise<number> {
    const monthStart = new Date();
    monthStart.setDate(1);
    monthStart.setHours(0, 0, 0, 0);

    const data = await this.generationRepo
      .createQueryBuilder('g')
      .where('g.timestamp >= :monthStart', { monthStart })
      .getMany();

    const monthlyEnergy = data.reduce((sum, d) => sum + d.dailyEnergy, 0); // MWh
    const hoursInMonth = 730;
    const installedCapacity = 7.425; // MW

    return (monthlyEnergy / (installedCapacity * hoursInMonth)) * 100;
  }

  /**
   * Calcula disponibilidade (uptime)
   */
  private async calculateAvailability(): Promise<number> {
    const oneDayAgo = new Date(Date.now() - 24 * 60 * 60 * 1000);

    const inverters = await this.inverterRepo
      .createQueryBuilder('inv')
      .where('inv.timestamp >= :oneDayAgo', { oneDayAgo })
      .getMany();

    const totalSamples = inverters.length;
    const onlineSamples = inverters.filter(i => i.status === 'online').length;

    return (onlineSamples / totalSamples) * 100;
  }

  /**
   * Salva dados históricos (TimescaleDB hypertable)
   */
  private async saveHistorical(data: any): Promise<void> {
    await this.generationRepo.save({
      ...data,
      createdAt: new Date(),
    });
  }

  /**
   * Retorna histórico 24h para gráficos
   */
  private async getHistorical24h(): Promise<any[]> {
    const oneDayAgo = new Date(Date.now() - 24 * 60 * 60 * 1000);

    return await this.generationRepo
      .createQueryBuilder('g')
      .select('DATE_TRUNC(\'hour\', g.timestamp)', 'hour')
      .addSelect('AVG(g.totalPower)', 'avgPower')
      .addSelect('SUM(g.dailyEnergy)', 'energy')
      .where('g.timestamp >= :oneDayAgo', { oneDayAgo })
      .groupBy('hour')
      .orderBy('hour', 'ASC')
      .getRawMany();
  }

  /**
   * Retorna energia do mês
   */
  private async getMonthlyEnergy(): Promise<number> {
    const monthStart = new Date();
    monthStart.setDate(1);
    monthStart.setHours(0, 0, 0, 0);

    const result = await this.generationRepo
      .createQueryBuilder('g')
      .select('SUM(g.dailyEnergy)', 'total')
      .where('g.timestamp >= :monthStart', { monthStart })
      .getRawOne();

    return result?.total || 0;
  }
}


// ============================================================================
// ARQUIVO 3: apps/api/src/modules/maintenance/preventive/preventive.scheduler.ts
// Agendador Manutenção Preventiva
// ============================================================================

import { Injectable, Logger } from '@nestjs/common';
import { Cron, CronExpression } from '@nestjs/schedule';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';

import { WorkOrder } from '../entities/work-order.entity';
import { MaintenanceLog } from '../entities/maintenance-log.entity';
import { NotificationService } from '../../alerts/notification.service';

interface MaintenanceTask {
  id: string;
  component: string;
  type: 'preventive' | 'inspection' | 'cleaning';
  frequency: 'daily' | 'weekly' | 'monthly' | 'quarterly' | 'annual';
  description: string;
  estimatedDuration: number; // minutos
  priority: 'low' | 'medium' | 'high';
  checklist: string[];
}

@Injectable()
export class PreventiveScheduler {
  private readonly logger = new Logger(PreventiveScheduler.name);

  // Plano de manutenção preventiva CD01
  private readonly maintenancePlan: MaintenanceTask[] = [
    {
      id: 'PREV-001',
      component: 'Painéis Fotovoltaicos',
      type: 'cleaning',
      frequency: 'monthly',
      description: 'Limpeza painéis solares (13.500 módulos)',
      estimatedDuration: 480, // 8 horas
      priority: 'high',
      checklist: [
        'Inspeção visual sujeira/sombreamento',
        'Limpeza com água desmineralizada',
        'Verificar fixações/estruturas',
        'Medir curva I-V (amostragem 1%)',
        'Inspeção termográfica (drone)',
      ],
    },
    {
      id: 'PREV-002',
      component: 'Inversores',
      type: 'inspection',
      frequency: 'quarterly',
      description: 'Inspeção inversores Sungrow (50 unidades)',
      estimatedDuration: 240,
      priority: 'high',
      checklist: [
        'Verificar logs erros',
        'Medir eficiência MPPT',
        'Inspeção visual ventiladores',
        'Limpar filtros ar',
        'Verificar conexões AC/DC',
        'Teste proteções (GFDI, anti-ilhamento)',
      ],
    },
    {
      id: 'PREV-003',
      component: 'BESS',
      type: 'inspection',
      frequency: 'monthly',
      description: 'Inspeção sistema armazenamento (2 containers)',
      estimatedDuration: 120,
      priority: 'high',
      checklist: [
        'Verificar SOC/SOH células',
        'Inspeção térmica (termografia)',
        'Verificar BMS (logs erros)',
        'Teste sistema refrigeração',
        'Verificar sistema incêndio',
        'Medir resistência isolação',
      ],
    },
    {
      id: 'PREV-004',
      component: 'Transformadores',
      type: 'inspection',
      frequency: 'quarterly',
      description: 'Inspeção transformadores elevadores',
      estimatedDuration: 90,
      priority: 'medium',
      checklist: [
        'Análise óleo isolante (cromatografia)',
        'Inspeção termográfica',
        'Verificar nível óleo',
        'Teste relé Buchholz',
        'Medir resistência terra',
      ],
    },
    {
      id: 'PREV-005',
      component: 'Sistema SCADA',
      type: 'preventive',
      frequency: 'monthly',
      description: 'Manutenção sistema supervisório',
      estimatedDuration: 60,
      priority: 'medium',
      checklist: [
        'Backup configurações',
        'Atualização firmware (se disponível)',
        'Verificar comunicação Modbus',
        'Teste alarmes',
        'Limpeza servidores (pó)',
      ],
    },
    {
      id: 'PREV-006',
      component: 'Estruturas',
      type: 'inspection',
      frequency: 'annual',
      description: 'Inspeção estruturas metálicas',
      estimatedDuration: 360,
      priority: 'medium',
      checklist: [
        'Inspeção visual corrosão',
        'Verificar aperto parafusos',
        'Medir torque conexões',
        'Pintura anticorrosiva (se necessário)',
        'Laudo estrutural (eng° civil)',
      ],
    },
  ];

  constructor(
    @InjectRepository(WorkOrder)
    private workOrderRepo: Repository<WorkOrder>,
    @InjectRepository(MaintenanceLog)
    private maintenanceLogRepo: Repository<MaintenanceLog>,
    private notificationService: NotificationService,
  ) {}

  /**
   * Executa todo dia 1º às 6h (criar WOs do mês)
   */
  @Cron('0 6 1 * *') // Min Hour Day Month DayOfWeek
  async scheduleMonthlyMaintenance() {
    this.logger.log('Agendando manutenções preventivas do mês');

    const monthlyTasks = this.maintenancePlan.filter(t => t.frequency === 'monthly');
    
    for (const task of monthlyTasks) {
      await this.createWorkOrder(task, new Date());
    }
  }

  /**
   * Executa toda segunda-feira às 6h (criar WOs da semana)
   */
  @Cron(CronExpression.EVERY_WEEK) // Segunda 00:00
  async scheduleWeeklyMaintenance() {
    this.logger.log('Agendando manutenções preventivas da semana');

    const weeklyTasks = this.maintenancePlan.filter(t => t.frequency === 'weekly');
    
    for (const task of weeklyTasks) {
      await this.createWorkOrder(task, new Date());
    }
  }

  /**
   * Executa todo dia às 6h (criar WOs diárias)
   */
  @Cron('0 6 * * *')
  async scheduleDailyMaintenance() {
    const dailyTasks = this.maintenancePlan.filter(t => t.frequency === 'daily');
    
    for (const task of dailyTasks) {
      await this.createWorkOrder(task, new Date());
    }
  }

  /**
   * Cria Work Order (Ordem de Serviço)
   */
  private async createWorkOrder(task: MaintenanceTask, scheduledDate: Date): Promise<void> {
    try {
      // Verificar se já existe WO para esta tarefa neste período
      const existingWO = await this.workOrderRepo.findOne({
        where: {
          taskId: task.id,
          scheduledDate,
          status: 'pending',
        },
      });

      if (existingWO) {
        this.logger.debug(`WO ${task.id} já existe para ${scheduledDate.toISOString()}`);
        return;
      }

      // Criar nova WO
      const workOrder = await this.workOrderRepo.save({
        taskId: task.id,
        component: task.component,
        type: task.type,
        description: task.description,
        scheduledDate,
        estimatedDuration: task.estimatedDuration,
        priority: task.priority,
        checklist: task.checklist,
        status: 'pending',
        assignedTo: null, // Atribuir manualmente ou via round-robin
        createdAt: new Date(),
      });

      this.logger.log(`WO criada: ${workOrder.id} - ${task.description}`);

      // Notificar equipe manutenção
      await this.notificationService.send({
        type: 'work_order_created',
        recipient: 'maintenance-team@barzel.com',
        subject: `Nova Ordem de Serviço: ${task.component}`,
        body: `
          Ordem: ${workOrder.id}
          Componente: ${task.component}
          Descrição: ${task.description}
          Data agendada: ${scheduledDate.toLocaleDateString('pt-BR')}
          Duração estimada: ${task.estimatedDuration} min
          Prioridade: ${task.priority}
        `,
      });
    } catch (error) {
      this.logger.error(`Erro criando WO ${task.id}: ${error.message}`, error.stack);
    }
  }

  /**
   * Verifica WOs atrasadas (executar diariamente)
   */
  @Cron('0 7 * * *')
  async checkOverdueWorkOrders() {
    const overdueWOs = await this.workOrderRepo
      .createQueryBuilder('wo')
      .where('wo.scheduledDate < :today', { today: new Date() })
      .andWhere('wo.status = :status', { status: 'pending' })
      .getMany();

    if (overdueWOs.length > 0) {
      this.logger.warn(`${overdueWOs.length} ordens de serviço atrasadas!`);

      // Notificar gerente manutenção
      await this.notificationService.send({
        type: 'overdue_work_orders',
        recipient: 'maintenance-manager@barzel.com',
        subject: `⚠️ ${overdueWOs.length} Ordens de Serviço Atrasadas`,
        body: overdueWOs.map(wo => 
          `- ${wo.id}: ${wo.description} (agendada: ${wo.scheduledDate.toLocaleDateString()})`
        ).join('\n'),
        priority: 'high',
      });
    }
  }
}


// ============================================================================
// ARQUIVO 4: ml/src/inference/predictor.py
// Serviço ML para Manutenção Preditiva
// ============================================================================

"""
Serviço de Inferência ML - Manutenção Preditiva
Modelos treinados: Detecção Anomalias + Previsão Falhas
"""

import numpy as np
import pandas as pd
from sklearn.ensemble import IsolationForest
from tensorflow.keras.models import load_model
import joblib
from datetime import datetime, timedelta
from typing import Dict, List, Tuple

class PredictiveMaintenance:
    def __init__(self):
        # Carregar modelos treinados
        self.anomaly_detector = joblib.load('../models/anomaly_detector.pkl')
        self.failure_predictor = load_model('../models/failure_predictor.h5')
        
        # Thresholds calibrados
        self.thresholds = {
            'anomaly_score': -0.5,  # Isolation Forest score
            'failure_probability': 0.7,  # 70% probabilidade
            'temperature_max': 75,  # °C (inversores)
            'efficiency_min': 0.95,  # 95% eficiência
        }
    
    def detect_anomalies(self, data: pd.DataFrame) -> List[Dict]:
        """
        Detecta anomalias em dados de monitoramento
        
        Args:
            data: DataFrame com features [power, temperature, voltage, current, efficiency]
        
        Returns:
            Lista de anomalias detectadas com score
        """
        # Features para modelo
        features = ['active_power', 'temperature', 'dc_voltage', 'dc_current', 'efficiency']
        X = data[features].fillna(data[features].mean())
        
        # Predição (Isolation Forest: -1 = anomalia, 1 = normal)
        predictions = self.anomaly_detector.predict(X)
        scores = self.anomaly_detector.score_samples(X)
        
        # Filtrar anomalias
        anomalies = []
        for idx, (pred, score) in enumerate(zip(predictions, scores)):
            if pred == -1 and score < self.thresholds['anomaly_score']:
                anomalies.append({
                    'timestamp': data.iloc[idx]['timestamp'],
                    'inverter_id': data.iloc[idx]['inverter_id'],
                    'anomaly_score': float(score),
                    'severity': 'high' if score < -0.8 else 'medium',
                    'features_anomalous': self._identify_anomalous_features(data.iloc[idx], features),
                    'recommendation': self._generate_recommendation(data.iloc[idx]),
                })
        
        return anomalies
    
    def predict_failures(self, historical_data: pd.DataFrame, horizon_days: int = 30) -> List[Dict]:
        """
        Prevê falhas nos próximos N dias usando LSTM
        
        Args:
            historical_data: Dados históricos (últimos 90 dias)
            horizon_days: Horizonte de previsão em dias
        
        Returns:
            Lista de componentes em risco com probabilidade falha
        """
        # Preparar sequências temporais (window=30 dias)
        window_size = 30
        sequences = self._create_sequences(historical_data, window_size)
        
        # Predição LSTM (output: probabilidade falha próximos N dias)
        predictions = self.failure_predictor.predict(sequences)
        
        # Identificar componentes em risco
        failures = []
        for idx, prob in enumerate(predictions):
            if prob[0] > self.thresholds['failure_probability']:
                inverter_id = historical_data.iloc[idx]['inverter_id']
                
                # Calcular tempo estimado até falha (TTF - Time To Failure)
                ttf_days = self._estimate_ttf(prob[0], historical_data.iloc[idx])
                
                failures.append({
                    'inverter_id': inverter_id,
                    'failure_probability': float(prob[0]),
                    'estimated_ttf_days': int(ttf_days),
                    'failure_date_estimate': (datetime.now() + timedelta(days=ttf_days)).isoformat(),
                    'recommended_action': self._get_maintenance_action(prob[0], ttf_days),
                    'confidence': 'high' if prob[0] > 0.85 else 'medium',
                })
        
        return failures
    
    def _identify_anomalous_features(self, row: pd.Series, features: List[str]) -> List[str]:
        """Identifica quais features estão anormais"""
        anomalous = []
        
        if row['temperature'] > self.thresholds['temperature_max']:
            anomalous.append('temperature_high')
        
        if row['efficiency'] < self.thresholds['efficiency_min']:
            anomalous.append('efficiency_low')
        
        # Z-score para detectar outliers em outras features
        for feat in ['active_power', 'dc_voltage', 'dc_current']:
            z_score = abs((row[feat] - row[feat].mean()) / row[feat].std())
            if z_score > 3:  # 3 desvios padrão
                anomalous.append(f'{feat}_outlier')
        
        return anomalous
    
    def _generate_recommendation(self, row: pd.Series) -> str:
        """Gera recomendação baseada em anomalia detectada"""
        if row['temperature'] > 70:
            return 'Verificar sistema de refrigeração. Possível obstrução ventiladores.'
        elif row['efficiency'] < 0.90:
            return 'Verificar conexões DC e limpeza painéis. Possível sombreamento.'
        elif row['dc_voltage'] < 500:
            return 'Tensão DC baixa. Verificar strings e bypass diodes.'
        else:
            return 'Inspeção visual geral recomendada.'
    
    def _create_sequences(self, data: pd.DataFrame, window_size: int) -> np.ndarray:
        """Cria sequências temporais para LSTM"""
        features = ['active_power', 'temperature', 'efficiency', 'daily_energy']
        X = data[features].values
        
        sequences = []
        for i in range(len(X) - window_size):
            sequences.append(X[i:i+window_size])
        
        return np.array(sequences)
    
    def _estimate_ttf(self, failure_prob: float, current_state: pd.Series) -> float:
        """
        Estima tempo até falha baseado em probabilidade e degradação
        
        Modelo simplificado: TTF = k / degradation_rate
        onde k é calibrado empiricamente
        """
        # Taxa de degradação (normalizada 0-1)
        degradation_rate = 1 - current_state['efficiency']
        
        # Fator calibração (dias)
        k = 60  # 60 dias de "margem" com 100% eficiência
        
        # TTF inversamente proporcional à degradação e probabilidade
        ttf = k * (1 - failure_prob) / max(degradation_rate, 0.01)
        
        return max(ttf, 1)  # Mínimo 1 dia
    
    def _get_maintenance_action(self, prob: float, ttf: int) -> str:
        """Retorna ação recomendada baseada em risco"""
        if prob > 0.9 or ttf < 7:
            return 'URGENTE: Manutenção corretiva imediata (parada programada)'
        elif prob > 0.8 or ttf < 14:
            return 'ALTA PRIORIDADE: Agendar manutenção esta semana'
        elif prob > 0.7 or ttf < 30:
            return 'MÉDIA PRIORIDADE: Agendar manutenção este mês'
        else:
            return 'BAIXA PRIORIDADE: Monitorar evolução'


# FastAPI endpoint para servir previsões
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel

app = FastAPI(title="CD01 Predictive Maintenance API")
predictor = PredictiveMaintenance()

class MonitoringData(BaseModel):
    inverter_id: int
    timestamp: str
    active_power: float
    temperature: float
    dc_voltage: float
    dc_current: float
    efficiency: float

@app.post("/predict/anomalies")
async def predict_anomalies(data: List[MonitoringData]):
    """Endpoint para detecção de anomalias em tempo real"""
    try:
        df = pd.DataFrame([d.dict() for d in data])
        anomalies = predictor.detect_anomalies(df)
        return {"anomalies": anomalies, "count": len(anomalies)}
    except Exception as e:
        raise HTTPException(status_code=500, detail=str(e))

@app.post("/predict/failures")
async def predict_failures(historical_data: List[MonitoringData], horizon_days: int = 30):
    """Endpoint para previsão de falhas"""
    try:
        df = pd.DataFrame([d.dict() for d in historical_data])
        failures = predictor.predict_failures(df, horizon_days)
        return {"predictions": failures, "horizon_days": horizon_days}
    except Exception as e:
        raise HTTPException(status_code=500, detail=str(e))


# ============================================================================
# ARQUIVO 5: docker-compose.yml
# Ambiente completo local
# ============================================================================

version: '3.8'

services:
  # PostgreSQL + TimescaleDB (Dados time-series)
  postgres:
    image: timescale/timescaledb:latest-pg16
    container_name: cd01-postgres
    environment:
      POSTGRES_DB: cd01_solar
      POSTGRES_USER: logiq
      POSTGRES_PASSWORD: ${POSTGRES_PASSWORD:-changeme}
    volumes:
      - postgres_data:/var/lib/postgresql/data
      - ./infra/docker/postgres/init.sql:/docker-entrypoint-initdb.d/init.sql
    ports:
      - "5432:5432"
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U logiq"]
      interval: 10s
      timeout: 5s
      retries: 5

  # Redis (Cache + PubSub)
  redis:
    image: redis:7-alpine
    container_name: cd01-redis
    command: redis-server --appendonly yes
    volumes:
      - redis_data:/data
    ports:
      - "6379:6379"
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]
      interval: 10s
      timeout: 3s
      retries: 5

  # API Backend (NestJS)
  api:
    build:
      context: .
      dockerfile: infra/docker/Dockerfile.api
    container_name: cd01-api
    environment:
      NODE_ENV: development
      DATABASE_URL: postgresql://logiq:${POSTGRES_PASSWORD:-changeme}@postgres:5432/cd01_solar
      REDIS_URL: redis://redis:6379
      JWT_SECRET: ${JWT_SECRET:-dev-secret-change-in-prod}
    volumes:
      - ./apps/api:/app
      - /app/node_modules
    ports:
      - "3001:3001"
    depends_on:
      postgres:
        condition: service_healthy
      redis:
        condition: service_healthy
    command: npm run start:dev

  # Frontend Web (Next.js)
  web:
    build:
      context: .
      dockerfile: infra/docker/Dockerfile.web
    container_name: cd01-web
    environment:
      NEXT_PUBLIC_API_URL: http://localhost:3001
      NEXT_PUBLIC_WS_URL: ws://localhost:3001
    volumes:
      - ./apps/web:/app
      - /app/node_modules
      - /app/.next
    ports:
      - "3000:3000"
    depends_on:
      - api
    command: npm run dev

  # ML Service (FastAPI + Python)
  ml-service:
    build:
      context: ./ml
      dockerfile: Dockerfile
    container_name: cd01-ml
    environment:
      MODEL_PATH: /app/models
    volumes:
      - ./ml:/app
      - ml_models:/app/models
    ports:
      - "8000:8000"
    command: uvicorn src.inference.api:app --host 0.0.0.0 --port 8000 --reload

  # Grafana (Visualização)
  grafana:
    image: grafana/grafana:latest
    container_name: cd01-grafana
    environment:
      GF_SECURITY_ADMIN_PASSWORD: ${GRAFANA_PASSWORD:-admin}
      GF_INSTALL_PLUGINS: grafana-clock-panel
    volumes:
      - grafana_data:/var/lib/grafana
      - ./infra/monitoring/grafana/dashboards:/etc/grafana/provisioning/dashboards
      - ./infra/monitoring/grafana/datasources:/etc/grafana/provisioning/datasources
    ports:
      - "3002:3000"
    depends_on:
      - postgres

  # Prometheus (Métricas)
  prometheus:
    image: prom/prometheus:latest
    container_name: cd01-prometheus
    volumes:
      - ./infra/monitoring/prometheus/prometheus.yml:/etc/prometheus/prometheus.yml
      - prometheus_data:/prometheus
    ports:
      - "9090:9090"
    command:
      - '--config.file=/etc/prometheus/prometheus.yml'
      - '--storage.tsdb.path=/prometheus'

  # pgAdmin (Database management)
  pgadmin:
    image: dpage/pgadmin4:latest
    container_name: cd01-pgadmin
    environment:
      PGADMIN_DEFAULT_EMAIL: admin@logiq.com
      PGADMIN_DEFAULT_PASSWORD: ${PGADMIN_PASSWORD:-admin}
    ports:
      - "5050:80"
    depends_on:
      - postgres

volumes:
  postgres_data:
  redis_data:
  grafana_data:
  prometheus_data:
  ml_models:

networks:
  default:
    name: cd01-network


# ============================================================================
# ARQUIVO 6: package.json (Root - Monorepo)
# ============================================================================

{
  "name": "cd01-solar-logiq-platform",
  "version": "1.0.0",
  "private": true,
  "workspaces": [
    "apps/*",
    "packages/*"
  ],
  "scripts": {
    "dev": "turbo run dev",
    "build": "turbo run build",
    "test": "turbo run test",
    "lint": "turbo run lint",
    "format": "prettier --write \"**/*.{ts,tsx,md}\"",
    "clean": "turbo run clean && rm -rf node_modules",
    "db:migrate": "cd apps/api && npm run migration:run",
    "db:seed": "cd apps/api && npm run seed:run",
    "docker:up": "docker-compose up -d",
    "docker:down": "docker-compose down",
    "docker:logs": "docker-compose logs -f"
  },
  "devDependencies": {
    "@turbo/gen": "^1.11.0",
    "turbo": "^1.11.0",
    "prettier": "^3.1.0",
    "typescript": "^5.3.0"
  },
  "engines": {
    "node": ">=20.0.0",
    "pnpm": ">=8.0.0"
  },
  "packageManager": "pnpm@8.14.0"
}


# ============================================================================
# ARQUIVO 7: README.md (Principal)
# ============================================================================

# 🌞 CD01 Solar + LOGIQ Platform

Sistema completo de monitoramento, manutenção e trading de energia para usina solar fotovoltaica 7,425 MWp + BESS 5 MWh.

## 🎯 Features

### Monitoramento Real-Time
- ⚡ Geração instantânea (50 inversores via Modbus)
- 🔋 BESS SOC e health monitoring
- 🌡️ Temperatura inversores e baterias
- 📊 Performance Ratio e Capacity Factor
- 🌤️ Integração estação meteorológica

### Manutenção Preditiva
- 🤖 ML: Detecção anomalias (Isolation Forest)
- 🔮 Previsão falhas (LSTM - 30 dias ahead)
- 📅 Agendamento automático manutenção preventiva
- ✅ Checklists digitais e Work Orders
- 📈 Histórico manutenções (MTBF, MTTR)

### Energy Trading
- 💹 Preços spot CCEE real-time
- 🎯 Otimização BESS (peak shaving)
- 📄 Contratos bilaterais (B2B matching)
- 💰 Dashboard financeiro (NOI, ROI)

### Analytics
- 📊 Relatórios CVM automatizados
- 📈 Dashboards executivos (Grafana)
- 🌍 ESG tracking (I-REC, carbon credits)
- 🔍 Root cause analysis (RCA)

## 🏗️ Arquitetura

```
┌─────────────┐
│  Next.js    │ ← Frontend (React 18 + Tailwind)
│  Dashboard  │
└──────┬──────┘
       │ REST + WebSocket
┌──────▼──────┐
│   NestJS    │ ← Backend API
│     API     │
└──────┬──────┘
       │
  ┌────┴─────┬──────────┬─────────┐
  │          │          │         │
┌─▼──┐   ┌──▼──┐   ┌──▼──┐   ┌──▼───┐
│ PG │   │Redis│   │SCADA│   │ ML   │
│+TS │   │     │   │Modbus   │FastAPI
└────┘   └─────┘   └─────┘   └──────┘
```

## 🚀 Quick Start

### Pré-requisitos
- Node.js 20+
- Python 3.11+
- Docker & Docker Compose
- pnpm 8+

### 1. Clone & Install
```bash
git clone https://github.com/barzel/cd01-solar-logiq.git
cd cd01-solar-logiq
pnpm install
```

### 2. Setup Environment
```bash
cp .env.example .env
# Editar .env com credenciais
```

### 3. Start Services
```bash
# Docker (PostgreSQL, Redis, Grafana)
docker-compose up -d

# Database migrations
pnpm db:migrate

# Seed demo data
pnpm db:seed
```

### 4. Run Development
```bash
# Todos os apps (Turborepo)
pnpm dev

# Acesso:
# - Frontend: http://localhost:3000
# - API: http://localhost:3001
# - ML Service: http://localhost:8000
# - Grafana: http://localhost:3002
# - pgAdmin: http://localhost:5050
```

## 📦 Stack Completo

### Frontend
- **Framework**: Next.js 14 (App Router)
- **UI**: shadcn/ui + Tailwind CSS
- **Charts**: Recharts
- **State**: Zustand
- **Forms**: React Hook Form + Zod

### Backend
- **Framework**: NestJS (TypeScript)
- **ORM**: TypeORM
- **Queue**: BullMQ
- **WebSocket**: Socket.io
- **Cache**: Redis

### Database
- **Primary**: PostgreSQL 16
- **Time-series**: TimescaleDB
- **Cache**: Redis

### ML/AI
- **Framework**: TensorFlow + scikit-learn
- **API**: FastAPI
- **Models**: 
  - Isolation Forest (anomaly detection)
  - LSTM (failure prediction)

### DevOps
- **Containers**: Docker + Kubernetes
- **CI/CD**: GitHub Actions
- **IaC**: Terraform (AWS)
- **Monitoring**: Prometheus + Grafana

## 📊 Dashboards Grafana

### 1. Solar Overview
- Geração em tempo real
- Performance Ratio histórico
- Disponibilidade (uptime)
- Alertas ativos

### 2. Inverters Health
- Status 50 inversores (heatmap)
- Temperatura vs eficiência
- Curvas I-V
- Logs erros

### 3. BESS Performance
- SOC/SOH trends
- Charge/discharge cycles
- Revenue from arbitrage
- Degradation forecast

### 4. Financial ROI
- Receita mensal (autoconsumo + venda)
- OPEX tracking
- Payback progress
- Valuation impact

## 🧪 Testing

```bash
# Unit tests
pnpm test

# E2E tests
pnpm test:e2e

# Coverage
pnpm test:cov
```

## 🚢 Deployment

### Staging
```bash
# Automático via GitHub Actions (merge to develop)
git push origin develop
```

### Production
```bash
# Manual approval required
gh workflow run deploy-production.yml
```

## 📖 Documentação

- [API Reference](./docs/API.md) - Swagger/OpenAPI
- [Architecture](./docs/ARCHITECTURE.md) - Diagramas
- [Maintenance Guide](./docs/MAINTENANCE.md) - Procedimentos O&M
- [Deployment](./docs/DEPLOYMENT.md) - Deploy guide

## 🤝 Contribuindo

1. Fork o projeto
2. Crie feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open Pull Request

## 📄 License

Proprietary - Barzel Properties © 2025

## 👥 Team

- **Product Owner**: Ricardo Oliveira (CFO Barzel)
- **Tech Lead**: LOGIQ Engineering
- **Maintainers**: Canadian Solar O&M Team

## 📞 Support

- Email: support@logiq.com.br
- Slack: #cd01-solar-support
- Emergency: +55 11 9-XXXX-XXXX (24/7)

---

**Powered by LOGIQ Platform** 🚀
