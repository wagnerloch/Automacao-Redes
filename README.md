# Automação e Programabilidade em Redes

Ambiente de simulação de redes da disciplina. Roda **no navegador**, sem
instalar nada na sua máquina.

[![Abrir no GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/wagnerloch/Automacao-Redes?quickstart=1)

## Como abrir

1. Crie uma conta em [github.com](https://github.com), se ainda não tiver.
2. Clique no botão acima, ou use o botão verde **Code** e a aba **Codespaces**.
3. Espere o ambiente abrir. É o editor VS Code dentro do navegador, com terminal.
4. Confirme que está tudo pronto:

```bash
containerlab version
```

O ambiente já vem com o [containerlab](https://containerlab.dev) e o Docker
instalados. Quem cuida disso é o arquivo `.devcontainer/devcontainer.json`.

## O laboratório

O arquivo `aula.clab.yml` descreve a topologia: dois computadores ligados por um
cabo virtual, cada um com o seu endereço IP.

```
  pc1 ------------------ pc2
  10.0.0.1/24      10.0.0.2/24
```

## Os comandos que importam

```bash
containerlab deploy -t aula.clab.yml      # sobe a topologia
containerlab inspect -t aula.clab.yml     # mostra o que subiu
containerlab destroy -t aula.clab.yml     # derruba tudo
```

Para entrar em um dos computadores e testar:

```bash
docker exec -it clab-aula-pc1 ping -c 3 10.0.0.2
docker exec -it clab-aula-pc1 bash
```

## Atividade da aula

1. Suba a topologia e confirme que o `pc1` fala com o `pc2`.
2. Acrescente um terceiro computador, `pc3`, com o endereço `10.0.0.3/24`.
3. Ligue o `pc3` ao `pc2` e suba de novo.
4. O `pc1` consegue falar com o `pc3`? Por quê?

## Ao terminar

Derrube o laboratório e **pare o Codespace**, para não gastar a sua cota:

```bash
containerlab destroy -t aula.clab.yml
```

Depois, em [github.com/codespaces](https://github.com/codespaces), clique nos
três pontos ao lado do seu Codespace e escolha **Stop codespace**.

> A conta gratuita do GitHub dá 120 horas de processador por mês. Em uma
> máquina de dois núcleos, isso equivale a cerca de 60 horas de uso.
