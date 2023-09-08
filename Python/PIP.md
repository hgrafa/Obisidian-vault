
![[Pasted image 20230510155124.png]]

## Motivação

O python instala todas as bibibliotecas no mesmo site(sítio). Para descobrir o caminho destas instalações:

```py
import site
site.getsitepackages()
```

- Não é possível cuidar de diferentes versões em um mesmo projeto, exemplo: não é possível ter pandas 1.4 e 2.0 num mesmo projeto
- Nossos pacotes ficam desorganizados, já que ocorre uma fusão de tudo.
- Bibliotecas podem acabar baixando outras que usam internamente, e ela pode precisar de diferentes versões. **Conflito interno de versões entre dependências mais robustas.**


## Solução

- [[VENV]]