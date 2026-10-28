# Consumo de combustível — Caminhões canavieiros CRV

Painel semanal: km/L (meta do indicador), L/t, raio, motor ocioso, paradas longas, faixa de RPM, excesso de RPM e motoristas.

**Período atual:** 19/10/2026 a 25/10/2026

- `index.html`: relatório semanal (padrão novo, igual ao de colhedoras e transbordos).
- `antigo.html`: versão anterior do relatório (com excessos de velocidade e evolução diária).
- `litros.html`: evolução de litros por frota.

## Bases
- **Indicador Consumo de Combustível — Caminhões Canavieiros (PDF)**: coluna SEMANA (km, diesel, km/L, toneladas, L/t, raio), agrupado por modelo.
- **Monit**: telemetria (estado, motor ligado, RPM, operação, motorista).

## Regras
- Meta de km/L do indicador (1,20): verde na meta ou acima.
- Motor ocioso = PARADA com motor ligado (Sim ou RPM ≥ 700); cada leitura vale até a próxima (máx. 10 min); 90 s descontados de cada parada. Meta 10%.
- RPM: até 900 (lenta), 901–1.400, 1.401–1.750, 1.751–2.000, acima de 2.000 (excesso).
- Rankings de excesso de RPM (caminhões e motoristas): pelo menos 20 h de motor ligado. Ranking de ocioso por motorista: pelo menos 5 h.
- Rankings por caminhão são clicáveis e mostram os motoristas daquele caminhão.
- Turnos: A 07–15h, B 15–23h, C 23–07h.

## Como gerar
```
python gerar/gerar_relatorio.py --pdf INDICADOR_CAMINHOES.pdf --monit MONIT.csv [MONIT2.csv ...]
```
Precisa de Python 3 e `pdftotext` (poppler-utils). Visual em `gerar/modelo.html` (dados em `__DADOS__`).

Desenvolvido por João Vitor - CRV
