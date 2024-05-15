# Relatório: Instrumentação de Métricas no .NET

Com este guia, aprendi como instrumentar métricas em aplicativos para monitoramento e diagnóstico usando a biblioteca de métricas do .NET.

## Conceitos aprendidos

As métricas são medidas quantitativas que ajudam a entender o desempenho e o comportamento de um sistema. Elas podem incluir contagens, tempos, tamanhos e outros valores que são fundamentais para monitorar e diagnosticar aplicativos.

A instrumentação de métricas envolve a coleta, armazenamento e análise de métricas em tempo real ou próximo disso. Isso permite que identifiquemos tendências, problemas de desempenho e anomalias em nosso sistema, ajudando-nos a tomar decisões informadas sobre otimizações e ajustes.

## Instalação da Biblioteca de Métricas do .NET

Antes de começar a instrumentar métricas da aplicação .NET, precisamos instalar a biblioteca de métricas do .NET. Para isso, adicionamos uma referência ao pacote NuGet `Microsoft.Extensions.Diagnostics.Metrics`.

Executei o seguinte comando no terminal:

```bash
dotnet add package Microsoft.Extensions.Diagnostics.Metrics
```

Isso adicionou a biblioteca de métricas do .NET ao nosso projeto, permitindo que começássemos a instrumentar métricas em nosso código.

## Instrumentação de Métricas

Agora que instalamos a biblioteca de métricas do .NET, podemos começar a instrumentar métricas em nosso aplicativo. 

### Instrumentação Manual

A instrumentação manual envolve a criação e registro de métricas em nosso código usando a API fornecida pela biblioteca de métricas do .NET. Isso nos permite capturar métricas específicas de nosso aplicativo, como contagens, tempos e tamanhos de dados.

Para instrumentar métricas manualmente, seguimos estas etapas:

1. Criamos uma instância de `Meter` para capturar métricas em nosso aplicativo.
2. Registramos métricas usando métodos específicos, como `Measure.Counter`, `Measure.Gauge` e `Measure.Histogram`.
3. Atualizamos métricas conforme necessário em nosso código.

```csharp
using Microsoft.Extensions.Diagnostics.Metrics;

class Program
{
    static void Main(string[] args)
    {
        // Criamos uma instância de Meter
        using var meter = new Meter("MeuAplicativo");

        // Registramos uma métrica de contagem
        var contador = meter.CreateCounter("MinhaContagem");

        // Incrementamos o contador
        contador.Increment();

        // Mais código do aplicativo...
    }
}
```

Isso cria uma métrica de contagem chamada "MinhaContagem" e a incrementa em 1. Podemos adicionar mais código para atualizar a métrica conforme necessário em nosso aplicativo.


## Exibir a nova métrica

Agora que instrumentamos uma nova métrica em nosso aplicativo, podemos exibi-la em um sistema de monitoramento ou ferramenta de análise. Existem várias ferramentas disponíveis que oferecem suporte à ingestão e exibição de métricas, como Prometheus, Grafana, Azure Monitor e muitas outras.

Consultamos a documentação da ferramenta de monitoramento ou análise que estamos usando para obter informações sobre como configurar a ingestão de métricas e criar painéis para visualizar nossas métricas em tempo real.
