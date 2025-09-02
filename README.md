# PORTSCAN-EM-PYTHON
Scanner de portas automatizado em Python. Este script educacional percorre todas as portas TCP de um host especificado, verificando quais estão abertas. Criado apenas para aprendizado, demonstra fundamentos de rede em Python, programação com sockets, loops e entrada de dados do usuário.

⚠️ Uso exclusivo para fins educacionais • Desenvolvido por M!ss s3c

📝 Guia: Criando e executando seu primeiro Portscan em Python

1. Criar o arquivo do script

No terminal, crie o arquivo:

nano portscan.py

2. Adicionar o código Python

Cole o seguinte código:

#!/usr/bin/python3
# Scanner de portas educacional em Python
# Uso: python3 portscan.py <host>

import socket
import sys

# Verifica se o host foi fornecido
if len(sys.argv) != 2:
    print("Uso: python3 portscan.py <host>")
    sys.exit(1)

host = sys.argv[1]

print(f"Iniciando varredura de portas em {host}...\n")

# Percorre todas as portas TCP
for port in range(1, 65536):
    meusocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    meusocket.settimeout(0.5)  # evita travamentos longos
    result = meusocket.connect_ex((host, port))
    if result == 0:
        print(f"Porta {port} [ABERTA]")
    meusocket.close()


⚠️ Observação: Este script não deve ser usado para varredura não autorizada. Serve apenas para aprendizado.

3. Dar permissão de execução (opcional)

Se quiser rodar diretamente como programa:

chmod +x portscan.py

4. Executar o script
python3 portscan.py 127.0.0.1

5. Exemplo de execução
Iniciando varredura de portas em 127.0.0.1...

Porta 22 [ABERTA]
Porta 80 [ABERTA]
Porta 443 [ABERTA]

👉 O que você aprendeu aqui

import socket → biblioteca para programação de rede em Python.

sys.argv → argumentos passados via linha de comando.

connect_ex() → verifica se a porta está aberta (retorna 0 se sim).

for loop → percorre todas as portas.

settimeout() → evita travamentos em portas não responsivas.

Sempre usar close() → para liberar recursos do socket.
