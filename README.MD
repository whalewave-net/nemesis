# Get a signed ssh certificate
sudo rm -rf ~/.ssh/id_rsa-cert.pub && vault write -field=signed_key ssh/sign/shellwhale public_key=@$HOME/.ssh/id_rsa.pub > ~/.ssh/id_rsa-cert.pub && chmod 400 ~/.ssh/id_rsa-cert.pub

# Bootstrap a machine
ansible-playbook playbook.yml --user shellwhale --inventory inventory.ini --extra-vars "cloudflare_api_key=[REDACTED] vault_token=[REDACTED]"
