    # =============================================================
    # ESTRUTURA COMPLETA GIT PROJECT
    # Projeto: CD01 Solar + LOGIQ Platform
    # Stack: Monorepo (Turborepo) | Next.js + NestJS + PostgreSQL
    # =============================================================
    
    cd01-solar-logiq-platform/
    │
    ├─── .github/                              # GitHub Actions CI/CD
    │    ├─── workflows/
    │    │    ├─── ci.yml                      # Testes + Lint em PRs
    │    │    ├─── deploy-staging.yml          # Deploy automático staging
    │    │    ├─── deploy-production.yml       # Deploy produção (manual)
    │    │    ├─── security-scan.yml           # Snyk + Dependabot
    │    │    └─── backup-db.yml               # Backup diário PostgreSQL
    │    │
    │    ├─── ISSUE_TEMPLATE/
    │    │    ├─── bug_report.md
    │    │    ├─── feature_request.md
    │    │    └─── maintenance_alert.md        # Template alertas manutenção
    │    │
    │    └─── pull_request_template.md
    │
    ├─── docs/                                 # Documentação completa
    │    ├─── README.md                        # Visão geral projeto
    │    ├─── ARCHITECTURE.md                  # Diagrama arquitetura
    │    ├─── API.md                           # Documentação API (Swagger)
    │    ├─── DEPLOYMENT.md                    # Deploy guide
    │    ├─── MAINTENANCE.md                   # Procedimentos O&M
    │    │
    │    ├─── engineering/                     # Documentação engenharia
    │    │    ├─── electrical-design.md        # Projeto elétrico
    │    │    ├─── mechanical-specs.md         # Specs mecânicas
    │    │    ├─── bom-bill-of-materials.xlsx  # Lista equipamentos
    │    │    ├─── single-line-diagram.pdf     # Diagrama unifilar
    │    │    ├─── layout-autocad.dwg          # Layout AutoCAD
    │    │    └─── datasheets/                 # Datasheets equipamentos
    │    │         ├─── jinko-550wp.pdf
    │    │         ├─── sungrow-inverter.pdf
    │    │         └─── catl-bess.pdf
    │    │
    │    ├─── operations/                      # Manuais operacionais
    │    │    ├─── startup-procedure.md        # Procedimento inicialização
    │    │    ├─── shutdown-procedure.md       # Desligamento emergência
    │    │    ├─── troubleshooting.md          # Guia resolução problemas
    │    │    └─── preventive-maintenance.md   # Checklist manutenção
    │    │
    │    └─── compliance/                      # Documentos regulatórios
    │         ├─── aneel-registration.pdf      # Registro ANEEL
    │         ├─── enel-connection.pdf         # Parecer acesso Enel
    │         ├─── fire-department-avcb.pdf    # AVCB Bombeiros
    │         └─── environmental-license.pdf   # Licença ambiental
    │
    ├─── apps/                                 # Aplicações (Monorepo)
    │    │
    │    ├─── web/                             # Frontend Dashboard (Next.js 14)
    │    │    ├─── public/
    │    │    │    ├─── favicon.ico
    │    │    │    ├─── logo.svg
    │    │    │    └─── images/
    │    │    │         ├─── cd01-aerial.jpg   # Foto aérea CD
    │    │    │         └─── solar-panels.jpg
    │    │    │
    │    │    ├─── src/
    │    │    │    ├─── app/                   # Next.js App Router
    │    │    │    │    ├─── layout.tsx        # Root layout
    │    │    │    │    ├─── page.tsx          # Homepage
    │    │    │    │    │
    │    │    │    │    ├─── (auth)/           # Auth routes
    │    │    │    │    │    ├─── login/
    │    │    │    │    │    └─── register/
    │    │    │    │    │
    │    │    │    │    ├─── dashboard/        # Main dashboard
    │    │    │    │    │    ├─── page.tsx     # Overview
    │    │    │    │    │    ├─── layout.tsx   # Dashboard layout
    │    │    │    │    │    │
    │    │    │    │    │    ├─── monitoring/  # Real-time monitoring
    │    │    │    │    │    │    ├─── page.tsx
    │    │    │    │    │    │    ├─── components/
    │    │    │    │    │    │    │    ├─── GenerationChart.tsx
    │    │    │    │    │    │    │    ├─── InverterStatus.tsx
    │    │    │    │    │    │    │    ├─── BESSStatus.tsx
    │    │    │    │    │    │    │    └─── WeatherWidget.tsx
    │    │    │    │    │    │    └─── hooks/
    │    │    │    │    │    │         └─── useRealtimeData.ts
    │    │    │    │    │    │
    │    │    │    │    │    ├─── maintenance/ # Manutenção
    │    │    │    │    │    │    ├─── page.tsx
    │    │    │    │    │    │    ├─── preventive/
    │    │    │    │    │    │    │    ├─── page.tsx
    │    │    │    │    │    │    │    └─── components/
    │    │    │    │    │    │    │         ├─── MaintenanceCalendar.tsx
    │    │    │    │    │    │    │         ├─── ChecklistForm.tsx
    │    │    │    │    │    │    │         └─── WorkOrderTable.tsx
    │    │    │    │    │    │    │
    │    │    │    │    │    │    ├─── predictive/
    │    │    │    │    │    │    │    ├─── page.tsx
    │    │    │    │    │    │    │    └─── components/
    │    │    │    │    │    │    │         ├─── AnomalyDetection.tsx
    │    │    │    │    │    │    │         ├─── MLPredictions.tsx
    │    │    │    │    │    │    │         └─── FailureForecast.tsx
    │    │    │    │    │    │    │
    │    │    │    │    │    │    └─── corrective/
    │    │    │    │    │    │         └─── page.tsx
    │    │    │    │    │    │
    │    │    │    │    │    ├─── analytics/   # Analytics & Reports
    │    │    │    │    │    │    ├─── page.tsx
    │    │    │    │    │    │    ├─── components/
    │    │    │    │    │    │    │    ├─── PerformanceRatio.tsx
    │    │    │    │    │    │    │    ├─── EnergyBalance.tsx
    │    │    │    │    │    │    │    ├─── FinancialROI.tsx
    │    │    │    │    │    │    │    └─── ExportReports.tsx
    │    │    │    │    │    │    └─── reports/
    │    │    │    │    │    │         ├─── daily/
    │    │    │    │    │    │         ├─── monthly/
    │    │    │    │    │    │         └─── annual/
    │    │    │    │    │    │
    │    │    │    │    │    ├─── trading/     # Energy trading
    │    │    │    │    │    │    ├─── page.tsx
    │    │    │    │    │    │    └─── components/
    │    │    │    │    │    │         ├─── SpotPriceChart.tsx
    │    │    │    │    │    │         ├─── TradingDesk.tsx
    │    │    │    │    │    │         └─── ContractManager.tsx
    │    │    │    │    │    │
    │    │    │    │    │    └─── settings/    # Configurações
    │    │    │    │    │         ├─── page.tsx
    │    │    │    │    │         ├─── users/
    │    │    │    │    │         ├─── alerts/
    │    │    │    │    │         └─── integrations/
    │    │    │    │    │
    │    │    │    │    └─── api/              # API Routes
    │    │    │    │         ├─── auth/[...nextauth].ts
    │    │    │    │         ├─── realtime/route.ts
    │    │    │    │         └─── export/route.ts
    │    │    │    │
    │    │    │    ├─── components/            # Shared components
    │    │    │    │    ├─── ui/               # shadcn/ui components
    │    │    │    │    │    ├─── button.tsx
    │    │    │    │    │    ├─── card.tsx
    │    │    │    │    │    ├─── dialog.tsx
    │    │    │    │    │    ├─── chart.tsx
    │    │    │    │    │    └─── ...
    │    │    │    │    │
    │    │    │    │    ├─── layout/
    │    │    │    │    │    ├─── Header.tsx
    │    │    │    │    │    ├─── Sidebar.tsx
    │    │    │    │    │    └─── Footer.tsx
    │    │    │    │    │
    │    │    │    │    └─── charts/
    │    │    │    │         ├─── LineChart.tsx
    │    │    │    │         ├─── AreaChart.tsx
    │    │    │    │         ├─── GaugeChart.tsx
    │    │    │    │         └─── HeatMap.tsx
    │    │    │    │
    │    │    │    ├─── lib/                   # Utilities
    │    │    │    │    ├─── utils.ts
    │    │    │    │    ├─── api.ts            # API client
    │    │    │    │    ├─── auth.ts           # Auth helpers
    │    │    │    │    └─── calculations.ts   # Energy calcs
    │    │    │    │
    │    │    │    ├─── hooks/                 # Custom hooks
    │    │    │    │    ├─── useWebSocket.ts   # Real-time WS
    │    │    │    │    ├─── useLocalStorage.ts
    │    │    │    │    └─── useDebounce.ts
    │    │    │    │
    │    │    │    ├─── stores/                # State management (Zustand)
    │    │    │    │    ├─── authStore.ts
    │    │    │    │    ├─── monitoringStore.ts
    │    │    │    │    └─── alertStore.ts
    │    │    │    │
    │    │    │    └─── types/                 # TypeScript types
    │    │    │         ├─── monitoring.ts
    │    │    │         ├─── maintenance.ts
    │    │    │         ├─── trading.ts
    │    │    │         └─── api.ts
    │    │    │
    │    │    ├─── package.json
    │    │    ├─── tsconfig.json
    │    │    ├─── tailwind.config.ts
    │    │    ├─── next.config.js
    │    │    └─── .env.local.example
    │    │
    │    ├─── api/                             # Backend API (NestJS)
    │    │    ├─── src/
    │    │    │    ├─── main.ts                # Entry point
    │    │    │    ├─── app.module.ts          # Root module
    │    │    │    │
    │    │    │    ├─── modules/
    │    │    │    │    │
    │    │    │    │    ├─── monitoring/       # Monitoramento
    │    │    │    │    │    ├─── monitoring.module.ts
    │    │    │    │    │    ├─── monitoring.controller.ts
    │    │    │    │    │    ├─── monitoring.service.ts
    │    │    │    │    │    ├─── monitoring.gateway.ts  # WebSocket
    │    │    │    │    │    ├─── dto/
    │    │    │    │    │    │    ├─── realtime-data.dto.ts
    │    │    │    │    │    │    └─── historical-data.dto.ts
    │    │    │    │    │    └─── entities/
    │    │    │    │    │         ├─── inverter.entity.ts
    │    │    │    │    │         ├─── bess.entity.ts
    │    │    │    │    │         └─── generation.entity.ts
    │    │    │    │    │
    │    │    │    │    ├─── maintenance/      # Manutenção
    │    │    │    │    │    ├─── maintenance.module.ts
    │    │    │    │    │    ├─── maintenance.controller.ts
    │    │    │    │    │    ├─── maintenance.service.ts
    │    │    │    │    │    ├─── preventive/
    │    │    │    │    │    │    ├─── preventive.service.ts
    │    │    │    │    │    │    └─── preventive.scheduler.ts
    │    │    │    │    │    ├─── predictive/
    │    │    │    │    │    │    ├─── predictive.service.ts
    │    │    │    │    │    │    └─── ml-model.service.ts
    │    │    │    │    │    ├─── dto/
    │    │    │    │    │    │    ├─── work-order.dto.ts
    │    │    │    │    │    │    └─── checklist.dto.ts
    │    │    │    │    │    └─── entities/
    │    │    │    │    │         ├─── work-order.entity.ts
    │    │    │    │    │         ├─── maintenance-log.entity.ts
    │    │    │    │    │         └─── spare-part.entity.ts
    │    │    │    │    │
    │    │    │    │    ├─── analytics/        # Analytics
    │    │    │    │    │    ├─── analytics.module.ts
    │    │    │    │    │    ├─── analytics.service.ts
    │    │    │    │    │    ├─── performance-ratio.service.ts
    │    │    │    │    │    └─── financial.service.ts
    │    │    │    │    │
    │    │    │    │    ├─── trading/          # Energy trading
    │    │    │    │    │    ├─── trading.module.ts
    │    │    │    │    │    ├─── trading.controller.ts
    │    │    │    │    │    ├─── trading.service.ts
    │    │    │    │    │    ├─── ccee-integration.service.ts
    │    │    │    │    │    └─── pricing.service.ts
    │    │    │    │    │
    │    │    │    │    ├─── alerts/           # Sistema alertas
    │    │    │    │    │    ├─── alerts.module.ts
    │    │    │    │    │    ├─── alerts.service.ts
    │    │    │    │    │    ├─── notification.service.ts
    │    │    │    │    │    └─── rules-engine.service.ts
    │    │    │    │    │
    │    │    │    │    ├─── integrations/     # Integrações externas
    │    │    │    │    │    ├─── scada/
    │    │    │    │    │    │    ├─── scada.module.ts
    │    │    │    │    │    │    ├─── modbus.service.ts
    │    │    │    │    │    │    └─── opcua.service.ts
    │    │    │    │    │    ├─── weather/
    │    │    │    │    │    │    └─── weather-api.service.ts
    │    │    │    │    │    └─── ccee/
    │    │    │    │    │         └─── ccee-api.service.ts
    │    │    │    │    │
    │    │    │    │    ├─── auth/             # Autenticação
    │    │    │    │    │    ├─── auth.module.ts
    │    │    │    │    │    ├─── auth.controller.ts
    │    │    │    │    │    ├─── auth.service.ts
    │    │    │    │    │    └─── strategies/
    │    │    │    │    │         ├─── jwt.strategy.ts
    │    │    │    │    │         └─── local.strategy.ts
    │    │    │    │    │
    │    │    │    │    └─── users/            # Usuários
    │    │    │    │         ├─── users.module.ts
    │    │    │    │         ├─── users.service.ts
    │    │    │    │         └─── entities/
    │    │    │    │              └─── user.entity.ts
    │    │    │    │
    │    │    │    ├─── common/                # Shared code
    │    │    │    │    ├─── decorators/
    │    │    │    │    ├─── filters/
    │    │    │    │    ├─── guards/
    │    │    │    │    ├─── interceptors/
    │    │    │    │    └─── pipes/
    │    │    │    │
    │    │    │    ├─── config/                # Configuração
    │    │    │    │    ├─── database.config.ts
    │    │    │    │    ├─── redis.config.ts
    │    │    │    │    └─── app.config.ts
    │    │    │    │
    │    │    │    └─── database/              # Database
    │    │    │         ├─── migrations/
    │    │    │         └─── seeds/
    │    │    │
    │    │    ├─── test/                       # Tests
    │    │    │    ├─── unit/
    │    │    │    ├─── integration/
    │    │    │    └─── e2e/
    │    │    │
    │    │    ├─── package.json
    │    │    ├─── tsconfig.json
    │    │    ├─── nest-cli.json
    │    │    └─── .env.example
    │    │
    │    └─── mobile/                          # Mobile App (React Native)
    │         ├─── ios/
    │         ├─── android/
    │         ├─── src/
    │         │    ├─── screens/
    │         │    ├─── components/
    │         │    └─── navigation/
    │         └─── package.json
    │
    ├─── packages/                             # Shared packages
    │    │
    │    ├─── ui/                              # Shared UI components
    │    │    ├─── src/
    │    │    │    ├─── components/
    │    │    │    ├─── hooks/
    │    │    │    └─── utils/
    │    │    ├─── package.json
    │    │    └─── tsconfig.json
    │    │
    │    ├─── shared-types/                    # Shared TypeScript types
    │    │    ├─── src/
    │    │    │    ├─── monitoring.ts
    │    │    │    ├─── maintenance.ts
    │    │    │    └─── index.ts
    │    │    ├─── package.json
    │    │    └─── tsconfig.json
    │    │
    │    ├─── config/                          # Shared config
    │    │    ├─── eslint-config/
    │    │    ├─── prettier-config/
    │    │    └─── tsconfig/
    │    │
    │    └─── calculations/                    # Energy calculations lib
    │         ├─── src/
    │         │    ├─── performance-ratio.ts
    │         │    ├─── capacity-factor.ts
    │         │    ├─── tir-vpl.ts
    │         │    └─── index.ts
    │         ├─── package.json
    │         └─── tsconfig.json
    │
    ├─── scripts/                              # Scripts utilitários
    │    ├─── setup-dev.sh                     # Setup ambiente dev
    │    ├─── backup-db.sh                     # Backup PostgreSQL
    │    ├─── restore-db.sh                    # Restore backup
    │    ├─── generate-reports.py             # Gerar relatórios (Python)
    │    ├─── migrate-data.ts                  # Migração dados
    │    └─── seed-demo-data.ts                # Popular dados demo
    │
    ├─── infra/                                # Infrastructure as Code
    │    │
    │    ├─── docker/                          # Docker configs
    │    │    ├─── Dockerfile.web              # Frontend
    │    │    ├─── Dockerfile.api              # Backend
    │    │    ├─── Dockerfile.ml               # ML service
    │    │    └─── docker-compose.yml
    │    │
    │    ├─── kubernetes/                      # K8s manifests
    │    │    ├─── deployments/
    │    │    │    ├─── web-deployment.yaml
    │    │    │    ├─── api-deployment.yaml
    │    │    │    └─── postgres-deployment.yaml
    │    │    ├─── services/
    │    │    ├─── ingress/
    │    │    ├─── configmaps/
    │    │    └─── secrets/
    │    │
    │    ├─── terraform/                       # Terraform (AWS)
    │    │    ├─── main.tf
    │    │    ├─── variables.tf
    │    │    ├─── outputs.tf
    │    │    ├─── modules/
    │    │    │    ├─── vpc/
    │    │    │    ├─── rds/
    │    │    │    ├─── eks/
    │    │    │    └─── s3/
    │    │    └─── environments/
    │    │         ├─── staging/
    │    │         └─── production/
    │    │
    │    └─── monitoring/                      # Monitoring configs
    │         ├─── prometheus/
    │         │    └─── prometheus.yml
    │         ├─── grafana/
    │         │    └─── dashboards/
    │         │         ├─── solar-overview.json
    │         │         ├─── inverters-health.json
    │         │         └─── bess-performance.json
    │         └─── alertmanager/
    │              └─── alertmanager.yml
    │
    ├─── ml/                                   # Machine Learning
    │    ├─── notebooks/                       # Jupyter notebooks
    │    │    ├─── exploratory-analysis.ipynb
    │    │    ├─── anomaly-detection.ipynb
    │    │    ├─── failure-prediction.ipynb
    │    │    └─── performance-forecast.ipynb
    │    │
    │    ├─── models/                          # Trained models
    │    │    ├─── anomaly_detector.pkl
    │    │    ├─── failure_predictor.h5
    │    │    └─── performance_lstm.pt
    │    │
    │    ├─── src/                             # ML service code
    │    │    ├─── train/
    │    │    │    ├─── anomaly_detection.py
    │    │    │    └─── failure_prediction.py
    │    │    ├─── inference/
    │    │    │    ├─── predictor.py
    │    │    │    └─── api.py                # FastAPI ML endpoint
    │    │    └─── preprocessing/
    │    │         └─── feature_engineering.py
    │    │
    │    ├─── requirements.txt                 # Python dependencies
    │    └─── Dockerfile
    │
    ├─── data/                                 # Data storage (gitignored)
    │    ├─── raw/                             # Raw data from SCADA
    │    ├─── processed/                       # Processed data
    │    ├─── exports/                         # Exported reports
    │    └─── backups/                         # Database backups
    │
    ├─── tests/                                # Integration tests
    │    ├─── e2e/                             # End-to-end tests
    │    ├─── load/                            # Load tests (k6)
    │    └─── security/                        # Security tests
    │
    ├─── config/                               # Config files raiz
    │    ├─── database.yml                     # DB config
    │    ├─── redis.yml                        # Redis config
    │    └─── monitoring.yml                   # Monitoring config
    │
    ├─── .gitignore
    ├─── .env.example                          # Environment variables template
    ├─── .prettierrc                           # Prettier config
    ├─── .eslintrc.js                          # ESLint config
    ├─── turbo.json                            # Turborepo config
    ├─── package.json                          # Root package.json
    ├─── pnpm-workspace.yaml                   # PNPM workspaces
    ├─── README.md                             # Project README
    └─── LICENSE
