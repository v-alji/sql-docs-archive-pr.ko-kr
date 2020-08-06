---
title: CLR 통합 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
author: rothja
ms.author: jroth
ms.openlocfilehash: d7187906f1376deb81ca7ff4770af7b12b63c022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735316"
---
# <a name="enabling-clr-integration"></a><span data-ttu-id="f1b52-102">CLR 통합 사용</span><span class="sxs-lookup"><span data-stu-id="f1b52-102">Enabling CLR Integration</span></span>
  <span data-ttu-id="f1b52-103">CLR(공용 언어 런타임) 통합 기능은 기본적으로 해제되어 있으며 CLR 통합을 사용하여 구현된 개체를 사용하려면 이 기능을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1b52-103">The common language runtime (CLR) integration feature is off by default, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="f1b52-104">CLR 통합을 사용 하도록 설정 하려면 **sp_configure** 저장 프로시저의 **clr enabled** 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1b52-104">To enable CLR integration, use the **clr enabled** option of the **sp_configure** stored procedure:</span></span>  
  
```  
  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'clr enabled', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="f1b52-105">Clr **enabled** 옵션을 0으로 설정 하 여 clr 통합을 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1b52-105">You can disable CLR integration by setting the **clr enabled** option to 0.</span></span> <span data-ttu-id="f1b52-106">CLR 통합 기능을 해제하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 모든 CLR 루틴 실행을 중지하고 모든 애플리케이션 도메인을 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f1b52-106">When you disable CLR integration, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stops executing all CLR routines and unloads all application domains.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1b52-107">CLR 통합을 사용 하도록 설정 하려면 **sysadmin** 및 **serveradmin** 고정 서버 역할의 멤버가 암시적으로 소유 하는 ALTER SETTINGS 서버 수준 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1b52-107">To enable CLR integration, you must have ALTER SETTINGS server level permission, which is implicitly held by members of the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1b52-108">많은 양의 메모리와 많은 수의 프로세서가 구성되어 있는 컴퓨터에서는 서버를 시작할 때 SQL Server의 CLR 통합 기능을 로드하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1b52-108">Computers configured with large amounts of memory and a large number of processors may fail to load the CLR integration feature of SQL Server when starting the server.</span></span> <span data-ttu-id="f1b52-109">이 문제를 해결 하려면 **-gmemory_to_reserve** 서비스 시작 옵션을 사용 하 여 서버를 시작 하 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 고 충분 한 크기의 메모리 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1b52-109">To address this issue, start the server by using the **-gmemory_to_reserve**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service startup option, and specify a memory value large enough.</span></span> <span data-ttu-id="f1b52-110">자세한 내용은 [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1b52-110">For more information, see [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1b52-111">경량 풀링에서는 CLR(공용 언어 런타임) 실행이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1b52-111">Common language runtime (CLR) execution is not supported under lightweight pooling.</span></span> <span data-ttu-id="f1b52-112">CLR 통합 기능을 설정하려면 먼저 경량 풀링 기능을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1b52-112">Before enabling CLR integration, you must disable lightweight pooling.</span></span> <span data-ttu-id="f1b52-113">자세한 내용은 [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1b52-113">For more information, see [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1b52-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f1b52-114">See Also</span></span>  
 <span data-ttu-id="f1b52-115">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f1b52-115">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="f1b52-116">[clr enabled 서버 구성 옵션](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="f1b52-116">[clr enabled Server Configuration Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) </span></span>  
 <span data-ttu-id="f1b52-117">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f1b52-117">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="f1b52-118">[GRANT&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f1b52-118">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 [<span data-ttu-id="f1b52-119">서버 수준 역할</span><span class="sxs-lookup"><span data-stu-id="f1b52-119">Server-Level Roles</span></span>](../security/authentication-access/server-level-roles.md)  
  
  
