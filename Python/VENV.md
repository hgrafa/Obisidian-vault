```bash
Set-ExecutionPolicy Unrestricted -Force
```
O Virtual Enviroment cria um ambiente falso, com um `sitepackages` particular para por apenas as dependências necessárias e bem resolvidas no projeto atual.

![[Pasted image 20230510162703.png]]

## venv VS. virtualenv

O **venv** pertence ao python por causa do desenvolvimento independente do **virtualenv**, sendo uma ferramenta mais completa, mais atualizada e em casos com demandas realmente especificas, mais velocidadade e mais segurança **daremos preferência ao virtualenv**, em qualquer outra situação usamos o **venv** integrado do python.

## Requirements

`requirements.txt` é um arquivo que determina quais são os elementos minimos e qual a versão adequada de cada coisa que deve ser instalada no nosso projeto.

[docs](https://pip.pypa.io/en/stable/reference/requirements-file-format/)

## Dev Requirements

Para colocar dependências referentes em nível de desenvolvimento, que não necessariamente irão para a produção, podemos criar um arquivo: `requirements_dev.txt`. Nele vamos indicar a instalação dos nosssos `requirements` e depois instalar os adicionais ao projeto.

```txt
# instala bibliotecas de producao
-r requirements.txt 

# instala bibliotecas de desenvolvimento
black
pytest
ipython
```

