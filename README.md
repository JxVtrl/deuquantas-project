
# Deu Quantas - Projeto Principal

Bem-vindo ao repositório principal do **Deu Quantas**, uma plataforma que promove transparência entre consumidores e estabelecimentos no controle de comandas. Este repositório gerencia os submódulos que compõem a aplicação, incluindo os frontends (web e mobile), backend e infraestrutura.

## 📚 Estrutura do Repositório

Este repositório utiliza **submódulos Git** para organizar os diferentes componentes da aplicação. Cada submódulo está vinculado a um repositório independente, permitindo modularidade e fácil manutenção.

### Submódulos

- **[Frontend Web](frontend-web/)**: Interface web para estabelecimentos e administradores. Desenvolvido em **Next.js**.
- **[Frontend Mobile](frontend-mobile/)**: Aplicativo mobile para consumidores. Desenvolvido em **React Native**.
- **[Backend](backend/)**: API central para gerenciar a lógica de negócios, pedidos e notificações. Desenvolvido em **Python**.
- **[Infraestrutura](infra/)**: Configurações de infraestrutura como código (IaC) usando ferramentas como Terraform e Docker.

---

## 🚀 Começando

Siga estas etapas para configurar o repositório localmente e inicializar todos os submódulos.

### Clonando o Repositório Principal com Submódulos

1. Clone o repositório principal com os submódulos:
   ```bash
   git clone --recurse-submodules git@github.com:JxVtrl/deuquantas-project.git
   cd deuquantas-project
   ```

2. Caso já tenha clonado o repositório principal sem os submódulos, inicialize-os manualmente:
   ```bash
   git submodule update --init --recursive
   ```

---

## 🔧 Scripts Úteis

### Atualizar os Submódulos
Para atualizar os submódulos para as versões mais recentes:
```bash
git submodule update --remote
```

### Adicionar Novos Submódulos
Se precisar adicionar novos repositórios como submódulos:
```bash
git submodule add git@github.com:JxVtrl/deuquantas-project.git <PASTA_DESTINO>
git commit -m "Adiciona novo submódulo: <NOME>"
```

---

## 📂 Estrutura do Projeto

```plaintext
deuquantas-project/
├── frontend-web/        # Submódulo para o frontend web
├── frontend-mobile/     # Submódulo para o frontend mobile
├── backend/             # Submódulo para o backend
├── infra/               # Submódulo para a infraestrutura
└── README.md            # Este arquivo
```

---

## 🛠 Tecnologias Utilizadas

O projeto utiliza as seguintes tecnologias:

- **Frontend Web**: [Next.js](https://nextjs.org/)
- **Frontend Mobile**: [React Native](https://reactnative.dev/)
- **Backend**: [Python](https://www.python.org/) e [Flask](https://flask.palletsprojects.com/)
- **Infraestrutura**: [Terraform](https://www.terraform.io/), [Ansible](https://www.ansible.com/), [Docker](https://www.docker.com/)

---

## 📄 Licença

Este projeto está licenciado sob a [MIT License](LICENSE).

---

## 🤝 Contribuindo

Contribuições são bem-vindas! Siga estas etapas:

1. Fork este repositório.
2. Crie uma branch para sua feature:
   ```bash
   git checkout -b minha-feature
   ```
3. Faça suas alterações e commit:
   ```bash
   git commit -m "Minha nova feature"
   ```
4. Envie sua branch:
   ```bash
   git push origin minha-feature
   ```
5. Abra um Pull Request.

---

## 🗂 Links Importantes

- [Documentação do Projeto](https://example.com/docs) *(substituir pelo link real, se houver)*
- [GitHub Issues](https://github.com/seu-org/deuquantas-project/issues)

---

## 🧑‍💻 Equipe

- **Product Owner**: Nome da Pessoa
- **Tech Lead**: Nome da Pessoa
- **Desenvolvedores**: Lista dos Desenvolvedores

---

Se precisar de mais informações, abra uma **issue** ou entre em contato com a equipe de desenvolvimento. 🚀
