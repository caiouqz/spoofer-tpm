<p align="center">
  <h1 align="center"> TPM SPOOFER</h1>
  <p align="center"><b>A Fast and Effective Method to Spoof TPM Using Linux Mint</b></p>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%20%2F%20Linux%20Mint-blue?style=for-the-badge&logo=linuxmint" alt="Platform">
  <img src="https://img.shields.io/badge/Status-Working-success?style=for-the-badge" alt="Status">
  <img src="https://img.shields.io/badge/Warning-One%20Time%20Use-critical?style=for-the-badge" alt="Warning">
</p>

---

<p align="center">
  · <a href="#-checking-current-tpm-windows">TPM Check</a> •
  <a href="#-requirements">Requirements</a> •
  <a href="#️-bios--windows-setup">Setup</a> •
  <a href="#-linux-mint-commands">Commands</a> •
  <a href="#-verification">Verification</a> •
  <a href="#️-disclaimer">Disclaimer</a>
</p>

---

🔍 1. Verificando o TPM Atual (Windows)
Antes de iniciar o processo, verifique o estado atual do seu TPM para confirmar a alteração posterior:

Abra o Prompt de Comando (CMD).

Navegue até o diretório onde o arquivo está salvo:

cd C:\Users\Administrator\Desktop\spoftpm

(Utilize o caminho correto onde o seu arquivo está salvo).

Execute o comando: TPM.EXE

O resultado exibido será semelhante a este (indicando o seu TPM banido atual):
MD5 21390298401251525 
SHA1 242452151356351253 
SHA256 532151535135135155

📦 Pré-requisitos
Linux Mint ISO: Baixar aqui

Pendrive Bootável: Pelo menos 4GB, gravado utilizando o Rufus.

⚙️ 2. Configurações na BIOS e Windows
No Windows, pressione Win + R, digite tpm.msc e selecione Limpar TPM. O seu PC será reiniciado (certifique-se de que o TPM já está habilitado na BIOS).

Entre na BIOS do seu computador:

Limpe o TPM por lá (se a opção estiver disponível).

Desative o Secure Boot.

Defina o pendrive com o Linux Mint como o dispositivo de boot primário (se o sistema não inicializar com o Secure Boot desativado, tente ativá-lo novamente).

💻 3. Executando os Comandos (Linux Mint)
Abra o terminal do Linux Mint e execute os comandos abaixo em sequência:]

apt update && upgrade
sudo su
apt install tpm2-tools
tpm2_clear
tpm2_createprimary -C e -g sha256 -G rsa -c primary.ctx
tpm2_readpublic -c primary.ctx -f pem -o endorsement_pub.pem
tpm2_createprimary -C e -g sh1 -G rsa -c primary.ctx
tpm2_createprimary -C e -g MD5 -G rsa -c primary.ctx
tpm2_evictcontrol -C o -c primary.ctx 0x81010001

✅ 4. Verificação Final
Saia do ambiente Linux e reinicie o computador de volta para o Windows.

Verifique novamente o status do seu TPM para confirmar a alteração.
