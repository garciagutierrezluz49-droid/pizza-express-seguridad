## Restricción de puertos (para informe)
sudo ufw --force enable
sudo ufw allow 443/tcp
sudo ufw deny 8081/tcp
sudo ufw deny 8082/tcp
sudo ufw deny 8083/tcp
sudo ufw status

sudo iptables -A INPUT -p tcp --dport 8081 -s 127.0.0.1 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 8081 -j DROP
sudo iptables -L -n -v

## Verificación TLS
openssl verify -CAfile certs/pizza-ca.crt certs/pizza.crt
curl -k https://localhost:443/api/clientes/
