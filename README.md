<p align="center">
  <a href="https://ag.tavardt.com/br/">
    <img src="https://ag.tavardt.com/img/tavardt-banner.png" alt="TAVARDT" width="1024" />
  </a>
</p>

# Inteligência e Modelagem Matemática de ROI em Mídia Paga

[![Calculadora ROI](https://img.shields.io/badge/TAVARDT-Calculadora%20ROI-5b3cf5.svg)](https://tools.tavardt.com/br/calculadora-roi-trafego-pago/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Mecanismo matemático determinístico para análise de ROAS, ROI e projeções de escala não lineares com fatores de retornos decrescentes em mídia paga.

A ferramenta capacita engenheiros de receita, líderes de tráfego de performance e analistas de dados com modelagem econométrica precisa para simular expansão orçamentária sem assumir retornos lineares. Desenvolvido sem qualquer dependência externa, o toolkit roda nativamente em Python e JavaScript.

***

## Fundamentos Algorítmicos e Modelagem Matemática

Projeções lineares em campanhas de tráfego pago geram distorções financeiras graves e falsas expectativas de lucro. Na prática, leilões de anúncios sofrem saturação de audiência, fadiga criativa e elevação contínua do custo marginal por aquisição.

* **Cálculo de ROAS Base**: Razão direta entre receita bruta e investimento em mídia (`revenue / spend`), mensurando a eficiência imediata.
* **Cálculo de ROI Base**: Retorno percentual líquido sobre o capital alocado (`((revenue - spend) / spend) * 100`), isolando o lucro real.
* **Projeção de Escala Não Linear**: Aplica o expoente algorítmico `(decay_factor - 1)` sobre a razão de investimento `(target_spend / current_spend)` para projetar a compressão de ROAS.
* **Perda de Eficiência Marginal**: Quantifica a redução percentual exata de eficiência decorrente da ampliação do orçamento pretendido.
* **Arquitetura Dupla Isomórfica**: Fórmulas matemáticas idênticas implementadas na biblioteca padrão Python (`roi_engine.py`) e em JavaScript puro (`calculator.js`).

***

## Matriz de Métricas e Modelagem Matemática

<table>
  <thead>
    <tr>
      <th align="left">Métrica / Parâmetro</th>
      <th align="left">Fórmula Algorítmica</th>
      <th align="left">Comportamento Matemático</th>
      <th align="left">Utilidade para Decisão Estratégica</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>ROAS Base</strong></td>
      <td><code>revenue / spend</code></td>
      <td>Razão linear de retorno bruto arredondada em duas casas decimais.</td>
      <td>Valida a eficiência operacional atual para cada unidade monetária aplicada.</td>
    </tr>
    <tr>
      <td><strong>ROI Base</strong></td>
      <td><code>((revenue - spend) / spend) * 100</code></td>
      <td>Margem percentual líquida resultante do investimento publicitário.</td>
      <td>Confirma a geração de lucro líquido após recuperação integral do capital.</td>
    </tr>
    <tr>
      <td><strong>Razão de Escala</strong></td>
      <td><code>target_spend / current_spend</code></td>
      <td>Multiplicador de crescimento do investimento em testes de escala.</td>
      <td>Indica a magnitude proporcional do aumento de orçamento nos leilões.</td>
    </tr>
    <tr>
      <td><strong>ROAS Projetado</strong></td>
      <td><code>current_roas * (spend_ratio ** (decay_factor - 1))</code></td>
      <td>Decaimento potencial derivado da saturação de público e atrito de lances.</td>
      <td>Evita superestimar receitas brutas durante acelerações orçamentárias agressivas.</td>
    </tr>
    <tr>
      <td><strong>Receita Projetada</strong></td>
      <td><code>target_spend * projected_roas</code></td>
      <td>Faturamento bruto estimado sob curva de retornos decrescentes.</td>
      <td>Permite calcular se a receita marginal absorve o aumento nos custos operacionais.</td>
    </tr>
    <tr>
      <td><strong>Perda de Eficiência</strong></td>
      <td><code>(1 - (projected_roas / current_roas)) * 100</code></td>
      <td>Contração percentual do ROAS base sob escala de orçamento.</td>
      <td>Mensa o custo exato de eficiência incorrido para adquirir volume adicional.</td>
    </tr>
  </tbody>
</table>

***

## Instalação e Guia Rápido de Execução

Requer Python 3.8 ou superior utilizando exclusivamente bibliotecas padrão (`sys`, `json`, `argparse`). Não requer instalação de pacotes externos via pip.

Clone o repositório e execute a análise inicial no terminal:

```bash
git clone https://github.com/TAVARDT-Brasil/ads-roi-intelligence-br.git
cd ads-roi-intelligence-br
python roi_engine.py -s 10000 -r 50000 -ts 25000
```

Para gerar a saída estruturada em JSON para pipelines automatizados:

```bash
python roi_engine.py -s 10000 -r 50000 -ts 25000 -j
```

Ajuste o fator de decaimento para simular cenários de alta saturação de público:

```bash
python roi_engine.py -s 10000 -r 50000 -ts 30000 -d 0.78
```

Para ambientes Node.js ou execução no navegador, utilize o arquivo `calculator.js`:

```javascript
const ROI_Calculator = require('./calculator.js');

const base = ROI_Calculator.calculateBaseMetrics(10000, 50000);
console.log('ROAS Base:', base.roas, 'ROI Base:', base.roi);

const projecao = ROI_Calculator.projectScale(10000, 25000, base.roas, 0.85);
console.log('ROAS Projetado:', projecao.projectedROAS);
console.log('Perda de Eficiência:', projecao.efficiencyLoss + '%');
```

Exemplo de payload JSON gerado:

```json
{
  "currency": "BRL",
  "current_spend": 10000.0,
  "current_revenue": 50000.0,
  "base_metrics": {
    "roas": 5.0,
    "roi": 400.0
  },
  "scaling_projection": {
    "target_spend": 25000.0,
    "decay_factor": 0.85,
    "projection": {
      "projected_roas": 4.36,
      "projected_revenue": 109000.0,
      "efficiency_loss": 12.8
    }
  }
}
```

***

## Perguntas Frequentes (FAQ Técnico)

### Como o fator de decaimento modela os retornos decrescentes na escala de anúncios?
O fator de decaimento (`-d`, padrão 0.85) atua como um expoente de potência `(decay_factor - 1)` sobre a razão de investimento. À medida que o orçamento cresce, a entrega marginal enfrenta custos mais altos e esgotamento de público, reduzindo o ROAS projetado conforme modelos econométricos comprovados.

### Quais são as diferenças práticas entre o script Python e o módulo JavaScript?
Ambas as ferramentas executam as mesmas fórmulas matemáticas e regras de precisão decimal. O script Python (`roi_engine.py`) destina-se a execuções em terminal e automações de infraestrutura, enquanto `calculator.js` pode ser incorporado diretamente em aplicações Node.js e painéis frontend.

### Como a saída JSON pode ser conectada a pipelines de BI e Data Lakes?
Ao utilizar o parâmetro `-j`, o script Python emite exclusivamente uma estrutura JSON válida na saída padrão. Esse fluxo pode ser direcionado para utilitários como jq ou ingerido nativamente por conectores de dados em ambientes como BigQuery, Databricks ou orquestradores em nuvem.

### Por que a ferramenta não utiliza dependências externas ou chamadas de API de terceiros?
A ausência de dependências externas garante execução determinística, ausência total de vulnerabilidades de supply chain e velocidade de cálculo instantânea. Isso possibilita rodar a ferramenta em ambientes fechados de CI/CD ou clusters com restrições severas de rede.

### Como o indicador de perda de eficiência previne a escala deficitária de campanhas?
A perda de eficiência marginal evidencia a contração percentual entre o rendimento atual e o rendimento projetado. Caso o ROAS recalculado atinja patamares inferiores à margem de contribuição mínima do produto, a equipe de marketing interrompe a injeção orçamentária antes de gerar prejuízo operacional.

***

## Consultoria em Engenharia de Receita

Para auditoria de contas de mídia, modelagem econométrica e escala de aquisição B2B no Brasil, consulte os engenheiros da **TAVARDT Brasil**.

***

## Links Úteis

* **Portal Corporativo:** https://ag.tavardt.com/br/
* **Suíte de Diagnósticos:** https://tools.tavardt.com/br/
* **Contato Técnico:** https://ag.tavardt.com/br/contato/

***

### Licença
Distribuído sob a Licença MIT.

***

© 2026 TAVARDT. Todos os direitos reservados.
