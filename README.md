# rapl_tdp
## Exibe o TDP (consumo de energia em watts) para CPUs Ryzen, com base no mangohud.

## Testado no Arch Linux e Debian, com Ryzen 3 3200G e um Ryzen 7 5700X.
### Usa como base o '/sys/class/powercap/intel-rapl\:0/energy_uj', que mede o consumo total em micro joules.
### Usando um calculo simples é possivel obter o valor atual em Watts, pelos meus testes tem um bom nivel de precisão.
https://www.kernel.org/doc/html/latest/power/powercap/powercap.html#monitoring-attributes
### É necessario que o arquivo 'energy_uj' tenha permissão de leitura para "outros", o arquivo UDEV facilita isso, ou manual, mas perde com reboot:
```
sudo chmod o+r /sys/class/powercap/intel-rapl\:0/energy_uj
```
### Caso você queira usar apenas com o Mangohud, apenas o arquivo do UDEV, já é o suficiente, o mangohud vai exibir o consumo.
```
sudo cp 99-rapl-permissions.rules /etc/udev/rules.d/
sudo udevadm control --reload-rules
sudo udevadm trigger
```

### rapl_tdp
```
# modo monitor, exibe continuamente
./rapl_tdp -m

# exibe uma vez
./rapl_tdp
```
