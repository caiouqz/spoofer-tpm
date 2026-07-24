<p align="center">
  <h1 align="center">🛡️ FAST TPM SPOOFER</h1>
  <p align="center"><b>A Fast and Effective Method to Spoof TPM Using Linux Mint</b></p>
</p>

<p align="center">
  <a href="https://www.linuxmint.com/"><img src="https://img.shields.io/badge/Linux%20Mint-Supported-13a10e?style=for-the-badge&logo=linuxmint&logoColor=white" alt="Linux Mint"></a>
  <a href="#-requirements"><img src="https://img.shields.io/badge/Requirements-Check-blue?style=for-the-badge&logo=windows&logoColor=white" alt="Requirements"></a>
  <a href="#️-disclaimer"><img src="https://img.shields.io/badge/Warning-One%20Time%20Use-critical?style=for-the-badge" alt="Warning"></a>
</p>

<p align="center">
  · <a href="#-checking-current-tpm-windows">TPM Check</a> · 
  <a href="#-requirements">Requirements</a> · 
  <a href="#️-bios--windows-setup">Setup</a> · 
  <a href="#-linux-mint-commands">Commands</a> · 
  <a href="#-verification">Verification</a> · 
  <a href="#️-disclaimer">Disclaimer</a>
</p>

---

## 🔍 Checking Current TPM (Windows)

Antes de iniciar o processo, verifique o estado atual do seu TPM para confirmar a alteração posterior:

1. Abra o **Prompt de Comando (CMD)**.
2. Navegue até o diretório onde o arquivo está salvo:
 2. Navegue até o diretório onde o arquivo está salvo:
cmd
cd C:\Users\Administrator\Desktop\spof tpm

após execute esse comando 
TPM.EXE

O seu atual TPM banido aparecerá assim:
MD5 21390298401251525 
SHA1 242452151356351253 
SHA256 532151535135135155

📦 Requirements
Linux Mint ISO: [Baixar aqui](https://www.linuxmint.com/edition.php?id=322)

Pendrive Bootável: Pelo menos 4GB, gravado utilizando o Rufus.

⚙️ BIOS & Windows Setup
No Windows, pressione Win + R → digite tpm.msc → Limpar TPM → o seu PC será reiniciado (certifique-se de que o TPM já está habilitado na BIOS).

Entre na BIOS do seu computador:

Limpe o TPM por lá (se a opção estiver disponível).

Desative o Secure Boot.

Defina o pendrive com o Linux Mint como o dispositivo de boot primário (se o sistema não inicializar com o Secure Boot desativado, tente ativá-lo novamente).

💻 Linux Mint Commands
Abra o terminal do Linux Mint e execute os comandos abaixo em sequência:
apt update && upgrade
sudo su
apt install tpm2-tools
tpm2_clear
tpm2_createprimary -C e -g sha256 -G rsa -c primary.ctx
tpm2_readpublic -c primary.ctx -f pem -o endorsement_pub.pem
tpm2_createprimary -C e -g sh1 -G rsa -c primary.ctx
tpm2_createprimary -C e -g MD5 -G rsa -c primary.ctx
tpm2_evictcontrol -C o -c primary.ctx 0x81010001

✅ Verification
Saia do ambiente Linux e reinicie o computador de volta para o Windows.

Verifique novamente o status do seu TPM para confirmar a alteração.

⚠️ Disclaimer
É possível alterar o seu TPM apenas uma vez utilizando este método — use-o com cautela!


   

   
