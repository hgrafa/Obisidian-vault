## Por que são mais leves?

Eles são processos no sistema, ao invés de sistemas operacionais completos. Existe **Isolamento** e ele é feito através do conceito de **namespaces**.

## Classificações do Isolamento

1. **PID** - Isolamento de processos rodando dentro do container.
2. **NET** - Isolamento das interfaces de rede.
3. **IPC** - Isolamento da comunicação entre processos e memória compartilhada
4. **MNT** - Isolamento do sistema de arquivos, pontos de montagem.
5. **UTS** - Isolamento do kernel. Container acaba se comporta como outro host.