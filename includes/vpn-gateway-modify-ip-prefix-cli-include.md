---
title: archivo de inclusión
description: archivo de inclusión
services: vpn-gateway
author: cherylmc
ms.service: vpn-gateway
ms.topic: include
ms.date: 03/21/2018
ms.author: cherylmc
ms.custom: include file, devx-track-azurecli
ms.openlocfilehash: 2b2c2a8f471aba36592f76caf46b7d26d7e3bb31
ms.sourcegitcommit: 8c7f47cc301ca07e7901d95b5fb81f08e6577550
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2020
ms.locfileid: "92755551"
---
### <a name="to-modify-local-network-gateway-ip-address-prefixes---no-gateway-connection"></a><a name="noconnection"></a>Para modificar los prefijos de dirección IP de la puerta de enlace de red local (sin conexión de puerta de enlace)

Si no dispone de una conexión de puerta de enlace y desea agregar o quitar prefijos de direcciones IP, utilice el mismo comando que se usa para crear la puerta de enlace de red local, [az network local-gateway create](https://docs.microsoft.com/cli/azure/network/local-gateway). Este comando también se puede usar para actualizar la dirección IP de la puerta de enlace del dispositivo VPN. Para sobrescribir la configuración actual, utilice el nombre existente de la puerta de enlace de red local. Si usa otro nombre, creará una nueva puerta de enlace de red local, en lugar de sobrescribir la existente.

Cada vez que se realiza un cambio, debe especificarse toda la lista de prefijos, no solo los prefijos que se desea cambiar. Especifique solo los prefijos que desea conservar. En este caso, 10.0.0.0/24 y 20.0.0.0/24

```azurecli
az network local-gateway create --gateway-ip-address 23.99.221.164 --name Site2 -g TestRG1 --local-address-prefixes 10.0.0.0/24 20.0.0.0/24
```

### <a name="to-modify-local-network-gateway-ip-address-prefixes---existing-gateway-connection"></a><a name="withconnection"></a>Para modificar los prefijos de dirección IP de la puerta de enlace de red local (conexión de puerta de enlace existente)

Si tiene una conexión de puerta de enlace y desea agregar o quitar prefijos de direcciones IP, estos se pueden actualizar mediante [az network local-gateway update](https://docs.microsoft.com/cli/azure/network/local-gateway). Esto tendrá como resultado un tiempo de inactividad para la conexión VPN. Al modificar los prefijos de direcciones IP, no preciso eliminar la puerta de enlace VPN.

Cada vez que se realiza un cambio, debe especificarse toda la lista de prefijos, no solo los prefijos que se desea cambiar. En este ejemplo, 10.0.0.0/24 y 20.0.0.0/24 ya están presentes. Agregamos los prefijos 30.0.0.0/24 y 40.0.0.0/24, y especificamos los cuatro prefijos al actualizar.

```azurecli
az network local-gateway update --local-address-prefixes 10.0.0.0/24 20.0.0.0/24 30.0.0.0/24 40.0.0.0/24 --name VNet1toSite2 -g TestRG1
```
