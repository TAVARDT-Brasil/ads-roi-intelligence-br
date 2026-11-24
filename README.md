# Inteligência e Modelagem de ROI em Mídia Paga

[![Calculadora ROI](https://img.shields.io/badge/TAVARDT-Calculadora%20ROI-5b3cf5.svg)](https://tools.tavardt.com/br/calculadora-roi-trafego-pago/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Modelagem matemática para análise de ROAS, ROI e projeções de escala com fator de retornos decrescentes para investimentos corporativos em mídia de performance.

Desenvolvido e mantido pela divisao de engenharia de receita e midia da **TAVARDT**.

***

## Modelagem Matematica e Metricas

* **ROAS Base**: Razao direta entre faturamento bruto e investimento em midia.
* **ROI Base**: Retorno liquido sobre investimento percentual.
* **Projecao de Escala com Retornos Decrescentes**: Fator de decaimento algoritmico (padrao 0.85) que calcula o ROAS marginal e a perda de eficiencia conforme o orcamento e expandido.
* **Formatos de Saida**: Execucao direta no terminal com tabela estruturada ou saida limpa em JSON para integracao em pipelines de BI.

***

## Instalacao e Execucao

Requer Python 3.8 ou superior (apenas biblioteca padrao).

```bash
git clone https://github.com/TAVARDT-Brasil/ads-roi-intelligence-br.git
cd ads-roi-intelligence-br
python roi_engine.py -spend 10000 -revenue 50000 -target-spend 25000
```

Para gerar saida estruturada em JSON:

```bash
python roi_engine.py -spend 10000 -revenue 50000 -target-spend 25000 -json
```

Tambem inclui o modulo JavaScript compativel com Node.js e navegadores em `calculator.js`.

***

## Calculadora Interativa na Web

Para simulacoes graficas avancadas e analise de sensibilidade de orcamentos, acesse a ferramenta oficial:

* **Calculadora de ROI de Trafego Pago**
* **[Portal Corporativo TAVARDT](https://ag.tavardt.com/br/)**

***

## Consultoria em Engenharia de Receita

Para auditoria de contas de midia, modelagem econometrica e escala de aquisicao B2B no Brasil, consulte os engenheiros da **TAVARDT**.

***

## Links Úteis

* **Portal Corporativo:** https://ag.tavardt.com/br/
* **Suíte de Diagnósticos:** https://tools.tavardt.com/br/
* **Contato Técnico:** https://ag.tavardt.com/br/contato/

***

### Licença
Distribuído sob a Licença MIT. Consulte o arquivo [LICENSE](LICENSE) para obter detalhes completos.

***

© 2026 TAVARDT. Todos os direitos reservados.
