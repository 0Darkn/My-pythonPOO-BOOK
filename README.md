
POO (Programação Orientada a Objetos) 

---

🧠 1️⃣ O que é POO?

POO (Programação Orientada a Objetos) é um paradigma baseado em:

Conceito	Explicação

Classe	Molde / estrutura
Objeto	Instância da classe
Atributos	Dados do objeto
Métodos	Funções da classe
Encapsulamento	Proteger dados
Herança	Reutilizar código
Polimorfismo	Mesmo método, comportamentos diferentes
Abstração	Esconder complexidade



---

🎯 2️⃣ O que vamos desenvolver?

Vamos criar um Sistema de Indexação em POO, que:

Indexa ficheiros

Organiza metadados

Permite pesquisa

Permite listar por tamanho

Guarda e carrega JSON

Usa encapsulamento corretamente

Está preparado para evoluir (SQLite, Flask, Qt)



---

📁 Estrutura do Projeto

python_index_poo/
│
├── main.py
├── models.py
├── index_manager.py
└── README.md


---

🧱 3️⃣ Desenvolvimento POO


---

📦 models.py

Classe que representa um ficheiro

import os
from datetime import datetime

class File:
    def __init__(self, path: str):
        self._path = path
        self._name = os.path.basename(path)
        self._size = os.path.getsize(path)
        self._created = datetime.fromtimestamp(os.path.getctime(path))

    # Encapsulamento com propriedades
    @property
    def name(self):
        return self._name

    @property
    def size(self):
        return self._size

    @property
    def path(self):
        return self._path

    def to_dict(self):
        return {
            "name": self._name,
            "path": self._path,
            "size": self._size,
            "created": self._created.strftime("%Y-%m-%d %H:%M:%S")
        }

    def __str__(self):
        return f"{self._name} | {self._size} bytes"


---

📦 index_manager.py

Classe responsável pelo controlo do índice

import os
import json
from models import File

class IndexManager:
    def __init__(self):
        self._files = []

    def index_directory(self, directory: str):
        if not os.path.exists(directory):
            raise FileNotFoundError("Diretório não encontrado.")

        for root, _, files in os.walk(directory):
            for file in files:
                full_path = os.path.join(root, file)
                try:
                    file_obj = File(full_path)
                    self._files.append(file_obj)
                except Exception:
                    pass

    def list_all(self):
        return self._files

    def search(self, keyword: str):
        return [f for f in self._files if keyword.lower() in f.name.lower()]

    def filter_by_size(self, min_size: int):
        return [f for f in self._files if f.size >= min_size]

    def save(self, filename="index.json"):
        with open(filename, "w", encoding="utf-8") as f:
            json.dump([file.to_dict() for file in self._files], f, indent=4)

    def load(self, filename="index.json"):
        with open(filename, "r", encoding="utf-8") as f:
            data = json.load(f)
            self._files = data


---

📦 main.py

Interface simples CLI

from index_manager import IndexManager

def main():
    manager = IndexManager()

    print("=== SISTEMA DE INDEXAÇÃO POO ===")

    directory = input("Caminho da pasta: ")
    manager.index_directory(directory)
    manager.save()

    print("Indexação concluída!")

    while True:
        print("\n1 - Listar")
        print("2 - Pesquisar")
        print("3 - Filtrar por tamanho")
        print("0 - Sair")

        option = input("Escolha: ")

        if option == "1":
            for file in manager.list_all():
                print(file)

        elif option == "2":
            keyword = input("Pesquisar: ")
            results = manager.search(keyword)
            for file in results:
                print(file)

        elif option == "3":
            size = int(input("Tamanho mínimo (bytes): "))
            results = manager.filter_by_size(size)
            for file in results:
                print(file)

        elif option == "0":
            break

if __name__ == "__main__":
    main()


---

🔍 4️⃣ Onde está a POO aqui?

✔ Encapsulamento

Uso de _atributos + @property

✔ Responsabilidade Única

File → representa ficheiro

IndexManager → gere o índice

main → interface


✔ Abstração

O utilizador não precisa saber como funciona os.walk

✔ Modularidade

Cada ficheiro tem uma responsabilidade


---

🚀 5️⃣ Como tornar profissional para GitHub

Adicionar:

README.md

# Python Index POO

Sistema de indexação desenvolvido em Python usando Programação Orientada a Objetos.

## Funcionalidades
- Indexação recursiva
- Pesquisa por nome
- Filtro por tamanho
- Exportação JSON

## Executar
python main.py


---

🧠 6️⃣ Evolução avançada (nível profissional)

Podemos adicionar:

SQLite (base de dados real)

Threading para indexação rápida

Interface Qt (GUI)

API REST com Flask

Logs

Sistema de autenticação

Testes unitários com pytest

Dockerfile

CI/CD GitHub Actions



---

📊 Arquitetura Final

[ File ]  --->  [ IndexManager ]  --->  [ Interface ]
   ↑              ↑
Modelo         Controlador


---
promo passo:

1. 🔥 Transformar isto numa aplicação Qt (como tu gostas)


2. 🔥 Criar versão com SQLite profissional


3. 🔥 Fazer versão Flask Web


4. 🔥 Fazer versão estilo motor de busca com ranking


5. 🔥 Integrar com logs avançados

