---
title: 'Versiones admitidas en Azure Database for PostgreSQL: servidor único'
description: 'Aquí se describen las versiones principales y secundarias de Postgres admitidas en Azure Database for PostgreSQL: servidor único.'
author: lfittl-msft
ms.author: lufittl
ms.service: postgresql
ms.topic: conceptual
ms.date: 07/22/2020
ms.custom: fasttrack-edit
ms.openlocfilehash: f03016c9a44968db49cd68bfec025c328861fc07
ms.sourcegitcommit: 7863fcea618b0342b7c91ae345aa099114205b03
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/03/2020
ms.locfileid: "93286427"
---
# <a name="supported-postgresql-major-versions"></a>Versiones principales de PostgreSQL admitidas

Consulte [Directiva de control de versiones de Azure Database for PostgreSQL](concepts-version-policy.md) para obtener detalles de la directiva de soporte técnico.

Azure Database for PostgreSQL actualmente admite las siguientes versiones principales:

## <a name="postgresql-version-11"></a>PostgreSQL, versión 11
La versión secundaria actual es la 11.6. Consulte la [documentación de PostgreSQL](https://www.postgresql.org/docs/11/static/release-11-6.html) para obtener más información sobre las mejoras y correcciones de esta versión secundaria.

## <a name="postgresql-version-10"></a>PostgreSQL, versión 10
La versión secundaria actual es la 10.11. Consulte la [documentación de PostgreSQL](https://www.postgresql.org/docs/10/static/release-10-11.html) para obtener más información sobre las mejoras y correcciones de esta versión secundaria.

## <a name="postgresql-version-96"></a>PostgreSQL, versión 9.6
La versión secundaria actual es la 9.6.16. Consulte la [documentación de PostgreSQL](https://www.postgresql.org/docs/9.6/static/release-9-6-16.html) para obtener más información sobre las mejoras y correcciones de esta versión secundaria.

## <a name="postgresql-version-95"></a>PostgreSQL, versión 9.5
La versión secundaria actual es la 9.5.20. Consulte la [documentación de PostgreSQL](https://www.postgresql.org/docs/9.5/static/release-9-5-20.html) para obtener información sobre las mejoras y correcciones de esta versión secundaria.

## <a name="managing-upgrades"></a>Administración de actualizaciones
El proyecto de PostgreSQL publica periódicamente versiones secundarias para corregir errores detectados. Azure Database for PostgreSQL aplica automáticamente revisiones a los servidores con versiones secundarias durante las implementaciones mensuales del servicio. 

No se admiten las actualizaciones locales automáticas de las versiones principales. Para actualizar a la siguiente versión principal, puede: 
   * Consulte [Actualizaciones de versiones principales con volcado y restauración](./how-to-upgrade-using-dump-and-restore.md).
   * Usar [pg_dump y pg_restore](./howto-migrate-using-dump-and-restore.md) para mover una base de datos a un servidor creado con la nueva versión del motor.
   * Como alternativa, puede actualizar de PostgreSQL 10 a 11 mediante el [servicio Azure Database Migration](..\dms\tutorial-azure-postgresql-to-azure-postgresql-online-portal.md).

### <a name="version-syntax"></a>Sintaxis de versión
Antes de la versión 10 de PostgreSQL, la [directiva de versiones de PostgreSQL](https://www.postgresql.org/support/versioning/) consideraba que una actualización de la _versión principal_ suponía un aumento en el primer _o_ segundo número. Por ejemplo, de 9.5 a 9.6 se consideraba una actualización de la versión _principal_. A partir de la versión 10, solo se considera una actualización de la versión principal un cambio en el primer número. Por ejemplo, de 10.0 a 10.1 es una actualización de versión _secundaria_. De la versión 10 a la 11 se consideraría una actualización de versión _principal_.

## <a name="next-steps"></a>Pasos siguientes
Para más información sobre las extensiones de PostgreSQL admitidas,consulte el [documento de extensiones](concepts-extensions.md).
