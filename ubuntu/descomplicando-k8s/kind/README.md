# kind
**kind** é ferramenta que permitir criar clusters k8s locais utilizando  contrineres Docker para simular o nodes do cluster. Esse abordagem simplifica o desenvolvimento e a execucao de aplicacoes em um ambiente k8s sem a necessidade de um cluster completo na nuvem ou em servidores dedicados.

## Criando Clusters Multi-Node com Kind

Para criar um cluster multi-node, voce pode usar um arquivo de configuracao YAML com o seguinte conteudo:

```yaml
   # Configuração de um cluster com três nós (dois workers)
   kind: Cluster
   apiVersion: kind.x-k8s.io/v1alpha4
   nodes:
    - role: control-plane
    - role: worker
    - role: worker
```

Crie o cluster execute o comando abaixo:
```bash
kind create cluster --config kind.yml --name <nome-do-cluster>
```

## Criando Clusters Multi-Node com Kind passando a version do k8s
Voce pode especificar a versao das imagens de contêiner dos node.
As tags de imagem disponíveis podem ser encotradas na pagina de [releases](https://github.com/kubernetes-sigs/kind/releases). É recomendável usar o hash SHA256 (shasum) para a versão desejada do Kubernetes. 

Exemplo de configuracao com versão especifica
```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
    - role: control-plane
      image: kindest/node:v1.16.4@sha256:b91a2c2317a000f3a783489dfb755064177dbc3a0b2f4147d50f04825d016f55
    - role: worker
      image: kindest/node:v1.16.4@sha256:b91a2c2317a000f3a783489dfb755064177dbc3a0b2f4147d50f04825d016f55
```
ou

```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
  - role: control-plane
    image: kindest/node:v1.25.0
  - role: worker
    image: kindest/node:v1.25.0
  - role: worker
    image: kindest/node:v1.25.0
```

Crie o cluster execute o comando abaixo:
```bash
kind create cluster --config kind.yml --name <nome-do-cluster>
```


[Documentacao do kind](https://kind.sigs.k8s.io/)