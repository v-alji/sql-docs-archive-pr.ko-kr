---
title: Database Mail XPs 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 33ee15e862e0992f39373ec30275040c4fcacc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652316"
---
# <a name="database-mail-xps-server-configuration-option"></a><span data-ttu-id="6de34-102">Database Mail XPs 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="6de34-102">Database Mail XPs Server Configuration Option</span></span>
  <span data-ttu-id="6de34-103">**DatabaseMail XPs** 옵션을 사용하여 서버에서 데이터베이스 메일을 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6de34-103">Use the **DatabaseMail XPs** option to enable Database Mail on this server.</span></span> <span data-ttu-id="6de34-104">사용 가능한 값은</span><span class="sxs-lookup"><span data-stu-id="6de34-104">The possible values are:</span></span>  
  
-   <span data-ttu-id="6de34-105">**0** 은 데이터베이스 메일을 사용할 수 없음을 나타냅니다(기본값).</span><span class="sxs-lookup"><span data-stu-id="6de34-105">**0** indicating Database Mail is not available (default).</span></span>  
  
-   <span data-ttu-id="6de34-106">**1** 은 데이터베이스 메일을 사용할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6de34-106">**1** indicating Database Mail is available.</span></span>  
  
 <span data-ttu-id="6de34-107">이 설정은 서버를 중지했다가 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6de34-107">The setting takes effect immediately without a server stop and restart.</span></span>  
  
 <span data-ttu-id="6de34-108">데이터베이스 메일을 활성화한 다음에는 데이터베이스 메일을 사용하도록 데이터베이스 메일 호스트 데이터베이스를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6de34-108">After enabling Database Mail, you must configure a Database Mail host database to use Database Mail.</span></span>  
  
 <span data-ttu-id="6de34-109">**데이터베이스 메일 구성 마법사** 를 사용하여 데이터베이스 메일을 구성하면 **msdb** 데이터베이스의 데이터베이스 메일 확장 저장 프로시저가 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="6de34-109">Configuring Database Mail using the **Database Mail Configuration Wizard** enables the Database Mail extended stored procedures in the **msdb** database.</span></span> <span data-ttu-id="6de34-110">**데이터베이스 메일 구성 마법사**를 사용하는 경우 다음의 **sp_configure** 예를 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6de34-110">If you use the **Database Mail Configuration Wizard**, you do not have to use the **sp_configure** example below.</span></span>  
  
 <span data-ttu-id="6de34-111">**Database Mail XPs** 옵션을 0으로 설정하면 데이터베이스 메일을 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6de34-111">Setting the **Database Mail XPs** option to 0 prevents Database Mail from starting.</span></span> <span data-ttu-id="6de34-112">옵션이 0인 상태에서 실행 중인 경우 **DatabaseMailExeMinimumLifeTime** 옵션에 구성된 시간 동안 유휴 상태가 될 때까지 계속 실행되면서 메일을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6de34-112">If it is running when the option is set to 0, it continues to run and send mail until it is idle for the time configured in the **DatabaseMailExeMinimumLifeTime** option.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6de34-113">예제</span><span class="sxs-lookup"><span data-stu-id="6de34-113">Examples</span></span>  
 <span data-ttu-id="6de34-114">다음 예에서는 데이터베이스 메일 확장 저장 프로시저를 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="6de34-114">The following example enables the Database Mail extended stored procedures.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Database Mail XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="6de34-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6de34-115">See Also</span></span>  
 [<span data-ttu-id="6de34-116">데이터베이스 메일</span><span class="sxs-lookup"><span data-stu-id="6de34-116">Database Mail</span></span>](../../relational-databases/database-mail/database-mail.md)  
  
  
