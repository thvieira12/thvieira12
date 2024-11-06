import tkinter as tk
from tkinter import messagebox

class Estoque:
    def __init__(self):
        self.ferramentas = {}

    def adicionar_ferramenta(self, nome, quantidade):
        if nome in self.ferramentas:
            self.ferramentas[nome] += quantidade
        else:
            self.ferramentas[nome] = quantidade
        return f"{quantidade} unidade(s) de '{nome}' adicionada(s) ao estoque."

    def remover_ferramenta(self, nome, quantidade):
        if nome in self.ferramentas and self.ferramentas[nome] >= quantidade:
            self.ferramentas[nome] -= quantidade
            if self.ferramentas[nome] == 0:
                del self.ferramentas[nome]
            return f"{quantidade} unidade(s) de '{nome}' removida(s) do estoque."
        else:
            return f"Não há quantidade suficiente de '{nome}' no estoque ou a ferramenta não existe."

    def exibir_estoque(self):
        if not self.ferramentas:
            return "O estoque está vazio."
        else:
            inventario = "Estoque atual:\n"
            for nome, quantidade in self.ferramentas.items():
                inventario += f"{nome}: {quantidade} unidade(s)\n"
            return inventario


class InterfaceEstoque:
    def __init__(self, root):
        self.estoque = Estoque()

        self.root = root
        self.root.title("Controle de Estoque de Ferramentas")

        # Nome da ferramenta
        tk.Label(root, text="Nome da Ferramenta:").grid(row=0, column=0)
        self.nome_entry = tk.Entry(root)
        self.nome_entry.grid(row=0, column=1)

        # Quantidade
        tk.Label(root, text="Quantidade:").grid(row=1, column=0)
        self.quantidade_entry = tk.Entry(root)
        self.quantidade_entry.grid(row=1, column=1)

        # Botão de Adicionar
        self.adicionar_btn = tk.Button(root, text="Adicionar", command=self.adicionar_ferramenta)
        self.adicionar_btn.grid(row=2, column=0, pady=5)

        # Botão de Remover
        self.remover_btn = tk.Button(root, text="Remover", command=self.remover_ferramenta)
        self.remover_btn.grid(row=2, column=1, pady=5)

        # Botão de Exibir Estoque
        self.exibir_btn = tk.Button(root, text="Exibir Estoque", command=self.exibir_estoque)
        self.exibir_btn.grid(row=3, column=0, columnspan=2, pady=5)

    def adicionar_ferramenta(self):
        nome = self.nome_entry.get()
        try:
            quantidade = int(self.quantidade_entry.get())
            if quantidade <= 0:
                raise ValueError("A quantidade deve ser positiva.")
            mensagem = self.estoque.adicionar_ferramenta(nome, quantidade)
            messagebox.showinfo("Sucesso", mensagem)
        except ValueError as e:
            messagebox.showerror("Erro", f"Entrada inválida: {e}")

    def remover_ferramenta(self):
        nome = self.nome_entry.get()
        try:
            quantidade = int(self.quantidade_entry.get())
            if quantidade <= 0:
                raise ValueError("A quantidade deve ser positiva.")
            mensagem = self.estoque.remover_ferramenta(nome, quantidade)
            messagebox.showinfo("Sucesso", mensagem)
        except ValueError as e:
            messagebox.showerror("Erro", f"Entrada inválida: {e}")

    def exibir_estoque(self):
        inventario = self.estoque.exibir_estoque()
        messagebox.showinfo("Estoque Atual", inventario)


# Criar a janela da interface
root = tk.Tk()
app = InterfaceEstoque(root)
root.mainloop()
- 👋 Hi, I’m @thvieira12
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
thvieira12/thvieira12 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
