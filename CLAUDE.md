# Relatório de consumo dos caminhões canavieiros (CRV)

Use sempre o gerador; não redesenhe a página à mão:
```
python3 gerar/gerar_relatorio.py --pdf <INDICADOR_CAMINHOES.pdf> --monit <MONIT.csv> [<MONIT2.csv> ...]
```
- Mesmo padrão dos relatórios de colhedoras e transbordos, adaptado para caminhão:
  - agrupado por modelo (FH 540, FMX 540…), como no PDF; consumo em km/L (meta 1,20, verde na meta ou acima), L/t e raio;
  - motor ocioso: PARADA com motor ligado, 90 s descontados de cada parada, meta 10%;
  - faixas de RPM (combinadas em 28/10/2026): até 900, 901–1.400, 1.401–1.750, 1.751–2.000, acima de 2.000 = excesso;
  - top 10 caminhões e top 10 motoristas em excesso de RPM (mín. 20 h); rankings clicáveis mostram os motoristas;
  - quadro "Com abastecimento, sem dados no Solinftec".
  - coluna "vs" no acompanhamento por caminhão (17/11/2026, igual às colhedoras): variação do km/L contra a semana anterior, por caminhão e no total do modelo; ▲ verde = subiu, ▼ vermelho = caiu. A semana anterior vem do `index.html` atual antes de ser substituído (se ele for da mesma semana, mantém a comparação que já tinha) ou de `--anterior <pagina.html>`. Gere as semanas em ordem para a comparação ficar certa.
- `antigo.html` é a versão anterior (excessos de velocidade); `litros.html` é separado. Não apagar.
- Assinatura: "Desenvolvido por João Vitor - CRV".
- Depois de mudar `gerar/modelo.html` ou `gerar/gerar_relatorio.py`, regenere, confira no navegador e faça commit e push.
