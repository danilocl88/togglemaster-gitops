# ToggleMaster GitOps

Repositório declarativo de deployment Kubernetes do ToggleMaster - FIAP Tech Challenge Fase 3.

## Fluxo

`togglemaster-apps` executa CI/DevSecOps, publica uma imagem imutável no Amazon ECR usando o SHA completo do commit e, em uma etapa posterior, atualiza este repositório.

ArgoCD observa este repositório e aplica automaticamente o estado desejado ao Amazon EKS.

## Segurança

Este repositório **não contém credenciais, passwords, API keys ou connection strings de banco**.

O Secret Kubernetes `togglemaster-runtime-secrets` é provisionado fora do Git e é pré-requisito do deployment.

O ConfigMap contém somente configuração operacional não sensível.

## Estrutura

- `apps/` - Deployments, Services e configuração não sensível.
- `bootstrap/` - inicialização idempotente dos bancos PostgreSQL e da service API key.
- `kustomization.yaml` - composição do estado desejado.

## Imagens

As imagens usam tags imutáveis baseadas em commit SHA. A tag `latest` não é utilizada.
