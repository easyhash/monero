# Daemon
```bash
docker run --name MoneroDaemon --volume daemon:/daemon/data easyhash/monero:latest /daemon/monerod --log-level=0 --rpc-bind-ip=0.0.0.0 --rpc-bind-port=18081 --data-dir=/daemon/data --confirm-external-bind --non-interactive
```

# Wallet
```bash
docker run --name MoneroWallet --volume wallet:/daemon/data --link MoneroDaemon:daemon easyhash/monero:latest /daemon/monero-wallet-rpc --log-level=0 --daemon-address=http://daemon:18081 --wallet-file=/daemon/data/monero.wallet --rpc-bind-ip=0.0.0.0 --rpc-bind-port=18082 --confirm-external-bind --disable-rpc-login --trusted-daemon --password '<wallet password>'
```