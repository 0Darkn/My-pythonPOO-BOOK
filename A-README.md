
📁 Estrutura profissional

🧱 Código organizado

📄 README completo

⚙️ .gitignore

🧪 Estrutura preparada para evoluir

🏷️ Boas práticas POO



---

📁 Estrutura Final do Projeto

python-index-poo/
│
├── src/
│   ├── __init__.py
│   ├── models.py
│   ├── index_manager.py
│   └── main.py
│
├── data/
│   └── index.json
│
├── tests/
│   └── test_index.py
│
├── .gitignore
├── requirements.txt
└── README.md


---

📦 src/models.py

import os
from datetime import datetime


class File:
    """
    Representa um ficheiro indexado.
    """

    def __init__(self, path: str):
        self._path = path
        self._name = os.path.basename(path)
        self._size = os.path.getsize(path)
        self._created = datetime.fromtimestamp(os.path.getctime(path))

    @property
    def name(self) -> str:
        return self._name

    @property
    def size(self) -> int:
        return self._size

    @property
    def path(self) -> str:
        return self._path

    def to_dict(self) -> dict:
        return {
            "name": self._name,
            "path": self._path,
            "size": self._size,
            "created": self._created.strftime("%Y-%m-%d %H:%M:%S"),
        }

    def __str__(self) -> str:
        return f"{self._name} | {self._size} bytes"


---

📦 src/index_manager.py

import os
import json
from .models import File


class IndexManager:
    """
    Responsável por gerir o índice de ficheiros.
    """

    def __init__(self):
        self._files = []

    def index_directory(self, directory: str) -> None:
        if not os.path.exists(directory):
            raise FileNotFoundError("Diretório não encontrado.")

        for root, _, files in os.walk(directory):
            for file in files:
                full_path = os.path.join(root, file)
                try:
                    file_obj = File(full_path)
                    self._files.append(file_obj)
                except Exception:
                    continue

    def list_all(self):
        return self._files

    def search(self, keyword: str):
        return [f for f in self._files if keyword.lower() in f.name.lower()]

    def filter_by_size(self, min_size: int):
        return [f for f in self._files if f.size >= min_size]

    def save(self, filename: str = "data/index.json") -> None:
        os.makedirs(os.path.dirname(filename), exist_ok=True)
        with open(filename, "w", encoding="utf-8") as f:
            json.dump([file.to_dict() for file in self._files], f, indent=4)

    def load(self, filename: str = "data/index.json") -> None:
        if not os.path.exists(filename):
            return
        with open(filename, "r", encoding="utf-8") as f:
            self._files = json.load(f)


---

📦 src/main.py

from .index_manager import IndexManager


def main():
    manager = IndexManager()

    print("=== Python Index POO ===")
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
            for file in manager.search(keyword):
                print(file)

        elif option == "3":
            size = int(input("Tamanho mínimo (bytes): "))
            for file in manager.filter_by_size(size):
                print(file)

        elif option == "0":
            break


if __name__ == "__main__":
    main()


---

📄 README.md (Profissional para GitHub)

# 📂 Python Index POO

Sistema de indexação de ficheiros desenvolvido em Python utilizando Programação Orientada a Objetos (POO).

---

## 🚀 Funcionalidades

- Indexação recursiva de diretórios
- Pesquisa por nome
- Filtro por tamanho
- Exportação para JSON
- Estrutura modular e escalável

---

## 🧱 Arquitetura

File → Modelo de ficheiro  
IndexManager → Controlador do índice  
Main → Interface CLI  

---

## ⚙️ Requisitos

Python 3.10+

---

## ▶️ Executar

```bash
python -m src.main


---

📁 Estrutura

src/
    models.py
    index_manager.py
    main.py


---

🔮 Melhorias Futuras

SQLite

Interface Qt

API Flask

Logs

Testes unitários

Docker


---

# 📄 .gitignore

pycache/ *.pyc *.pyo *.pyd *.log data/index.json .env venv/

---

# 📄 requirements.txt

Sem dependências externas

---

# 🧠 Porque esta estrutura é profissional?

✔ Usa package `src`  
✔ Usa imports relativos  
✔ Separação clara de responsabilidades  
✔ Diretório de dados separado  
✔ Preparado para testes  
✔ Preparado para publicação no GitHub  

---

próximo passo:

- 🔥 Transformar isto numa versão profissional com SQLite  
- 🔥 Criar versão com GUI Qt (como os teus projetos Windows 10)  
- 🔥 Criar versão Flask com API REST  
- 🔥 Adicionar logs e threading  
- 🔥 Criar setup.py para instalar como pacote  
