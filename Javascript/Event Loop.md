O event loop fica ouvindo a call stack (pilha de chamadas) das funções abertas.

O event loop é single thread, então fica buscando nesta pilha e distribuindo entre as outras threads disponíveis.

O javascript não é single thread, mas o event loop trabalha como uma distribuidora para outras threads.