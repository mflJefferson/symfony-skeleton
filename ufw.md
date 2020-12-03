### Primeiro passo checando se ufw está instalado e seu status

```
$   sudo ufw status
Status: inactive
```

### Se não tiver instalado, no ubuntu 20.04

```
$   sudo apt install ufw -y
```

### Para bloquear todas as conexões que estão vindo (incoming)

```
$   sudo ufw default deny incoming
```

### Para permitir todas as conexões saindo de seu despositivo (outgoing)

```
$   sudo ufw default allow outgoing
```

### Para adicionar um regra permitindo conexões por SSH

```
$   sudo ufw allow ssh
```

### Se sua porta SSH não for a padrão 22

```
$   sudo ufw allow <porta>/tcp comment 'SSH'
```

### Para ativar o ufw

```
$   sudo ufw enable
```

### Para permitir outras conexões
```
$   sudo ufw allow http comment 'SSH'
$   sudo ufw allow https comment 'SSH'
```

### Para permitir portas em ranges especificas

```
$   sudo ufw allow 6000:6007/tcp
$   sudo ufw allow 6000:6007/udp
```

#### Quando especificando regras em ranges, você também deve especificar o protocolo (tpc ou udp)

### IPs especificos

```
$   sudo ufw allow from 203.0.113.4
```

#### também é possivel criar uma regra especificando qual porta esse ip terá acesso

```
$   sudo ufw allow from 203.0.113.4 to any port 22
```
### Usando IPv6 com UFW
```
$   sudo nano /etc/default/ufw
IPV6=yes
```

### Negando conexões 
```
$   sudo ufw deny http
$   sudo ufw deny from 203.0.113.4
```

### Deletando regras
#### Comando para listar as regras
```
$   sudo status numbered
```
#### Saída
```
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 22                         ALLOW IN    15.15.15.0/24
[ 2] 80                         ALLOW IN    Anywhere
```
