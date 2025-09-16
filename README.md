# Loja-da-esquina
# Sistema simples de vendas com estoque

produtos = {}

def cadastrar_produto():
    nome = input("Nome do produto: ")
    if nome in produtos:
        print("⚠ Produto já cadastrado!")
        return
    quantidade = int(input("Quantidade em estoque: "))
    valor = float(input("Valor do produto: R$ "))
    produtos[nome] = {"estoque": quantidade, "valor": valor}
    print(f"✅ Produto '{nome}' cadastrado com sucesso!")

def listar_produtos():
    if not produtos:
        print("⚠ Nenhum produto cadastrado.")
        return
    print("\n📦 Lista de produtos:")
    for nome, dados in produtos.items():
        print(f"- {nome} | Estoque: {dados['estoque']} | Preço: R$ {dados['valor']:.2f}")

def vender_produto():
    listar_produtos()
    nome = input("\nDigite o nome do produto que deseja vender: ")
    if nome not in produtos:
        print("⚠ Produto não encontrado!")
        return
    quantidade = int(input("Quantidade a vender: "))
    if quantidade > produtos[nome]["estoque"]:
        print("⚠ Estoque insuficiente!")
        return
    total = quantidade * produtos[nome]["valor"]
    produtos[nome]["estoque"] -= quantidade
    print(f"✅ Venda realizada! Total: R$ {total:.2f}")
    if produtos[nome]["estoque"] == 0:
        print(f"⚠ O produto '{nome}' acabou no estoque!")

def menu():
    while True:
        print("\n--- Sistema de Vendas ---")
        print("1 - Cadastrar produto")
        print("2 - Listar produtos")
        print("3 - Vender produto")
        print("4 - Sair")
        opcao = input("Escolha uma opção: ")

        if opcao == "1":
            cadastrar_produto()
        elif opcao == "2":
            listar_produtos()
        elif opcao == "3":
            vender_produto()
        elif opcao == "4":
            print("🚪 Saindo do sistema...")
            break
        else:
            print("⚠ Opção inválida!")

menu()Estoque de venda e caderno de fiados

