import json

ARQUIVO = "usuarios.json"

# carregar usuários
def carregar_usuarios():
    try:
        with open(ARQUIVO, "r") as f:
            return json.load(f)
    except:
        return {}

# salvar usuários
def salvar_usuarios(usuarios):
    with open(ARQUIVO, "w") as f:
        json.dump(usuarios, f)

# cadastrar usuário
def cadastrar():
    usuarios = carregar_usuarios()
    
    user = input("Crie um usuário: ")
    
    if user in usuarios:
        print("Usuário já existe!")
        return
    
    senha = input("Crie uma senha: ")
    
    usuarios[user] = senha
    salvar_usuarios(usuarios)
    
    print("Usuário cadastrado com sucesso!")

# login
def login():
    usuarios = carregar_usuarios()
    
    user = input("Usuário: ")
    senha = input("Senha: ")
    
    if user in usuarios and usuarios[user] == senha:
        print("Login realizado com sucesso!")
    else:
        print("Usuário ou senha incorretos!")

# menu principal
while True:
    print("\n1 - Cadastrar")
    print("2 - Login")
    print("3 - Sair")
    
    opcao = input("Escolha: ")
    
    if opcao == "1":
        cadastrar()
    elif opcao == "2":
        login()
    elif opcao == "3":
        break
    else:
        print("Opção inválida!")
