---
title: cross db ownership chaining 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cross-database ownership chaining
- cross db ownership chaining option
- chaining ownership
ms.assetid: 7b2d49f2-b91c-4aee-a52b-6cc49bed03af
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cfb768065cc0aa2aaa7aed0f996b18e46f1da7ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651899"
---
# <a name="cross-db-ownership-chaining-server-configuration-option"></a><span data-ttu-id="13efb-102">cross db ownership chaining 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="13efb-102">cross db ownership chaining Server Configuration Option</span></span>
  <span data-ttu-id="13efb-103">**cross db ownership chaining** 옵션을 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 데이터베이스 간 소유권 체인을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13efb-103">Use the **cross db ownership chaining** option to configure cross-database ownership chaining for an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="13efb-104">이 서버 옵션을 사용하면 데이터베이스 수준에서 데이터베이스 간 소유권 체인을 제어하거나 모든 데이터베이스의 데이터베이스 간 소유권 체인을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13efb-104">This server option allows you to control cross-database ownership chaining at the database level or to allow cross-database ownership chaining for all databases:</span></span>  
  
-   <span data-ttu-id="13efb-105">인스턴스에 대해 **cross db ownership chaining** 이 해제(0) 상태일 때 모든 데이터베이스에 대해 데이터베이스 간 소유권 체인이 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="13efb-105">When **cross db ownership chaining** is off (0) for the instance, cross-database ownership chaining is disabled for all databases.</span></span>  
  
-   <span data-ttu-id="13efb-106">인스턴스에 대해 **cross db ownership chaining** 이 설정(1)되어 있으면 데이터베이스 간 소유권 체인이 모든 데이터베이스에 대해 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="13efb-106">When **cross db ownership chaining** is on (1) for the instance, cross-database ownership chaining is on for all databases.</span></span>  
  
-   <span data-ttu-id="13efb-107">ALTER DATABASE 문의 SET 절을 사용하여 개별 데이터베이스에 대해 데이터베이스 간 소유권 체인을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13efb-107">You can set cross-database ownership chaining for individual databases using the SET clause of the ALTER DATABASE statement.</span></span> <span data-ttu-id="13efb-108">새 데이터베이스를 만드는 경우 CREATE DATABASE 문을 사용하여 새 데이터베이스에 대해 데이터베이스 간 소유권 체인을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13efb-108">If you are creating a new database, you can set the cross-database ownership chaining option for the new database using the CREATE DATABASE statement.</span></span>  
  
     <span data-ttu-id="13efb-109">**인스턴스에서 호스트한 모든 데이터베이스가 데이터베이스 간 소유권 체인에 참여하지 않고 사용자가 이 설정에 따른 보안 위험을 잘 알고 있는 경우가 아니라면** cross db ownership chaining [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 1로 설정하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="13efb-109">Setting **cross db ownership chaining** to 1 is not recommended unless all of the databases hosted by the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must participate in cross-database ownership chaining and you are aware of the security implications of this setting.</span></span>  
  
## <a name="controlling-cross-database-ownership-chaining"></a><span data-ttu-id="13efb-110">데이터베이스 간 소유권 체인 제어</span><span class="sxs-lookup"><span data-stu-id="13efb-110">Controlling Cross-Database Ownership Chaining</span></span>  
 <span data-ttu-id="13efb-111">데이터베이스 간 소유권 체인을 설정하기 전에 다음 사항을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="13efb-111">Before turning cross-database ownership chaining on or off, consider the following:</span></span>  
  
-   <span data-ttu-id="13efb-112">데이터베이스 간 소유권 체인을 설정하거나 해제하려면 **sysadmin** 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13efb-112">You must be a member of the **sysadmin** fixed server role to turn cross-database ownership chaining on or off.</span></span>  
  
-   <span data-ttu-id="13efb-113">프로덕션 서버에서 데이터베이스 간 소유권 체인 설정을 해제하기 전에 타사 애플리케이션을 포함한 모든 애플리케이션을 테스트하여 설정 변경으로 인해 애플리케이션 기능이 영향받지 않도록 하십시오.</span><span class="sxs-lookup"><span data-stu-id="13efb-113">Before turning off cross-database ownership chaining on a production server, fully test all applications, including third-party applications, to ensure that the changes do not affect application functionality.</span></span>  
  
-   <span data-ttu-id="13efb-114">**sp_configure** 를 사용하여 RECONFIGURE를 지정하는 경우에는 서버를 실행하는 동안 **cross db ownership chaining**옵션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13efb-114">You can change the **cross db ownership chaining** option while the server is running if you specify RECONFIGURE with **sp_configure**.</span></span>  
  
-   <span data-ttu-id="13efb-115">데이터베이스 간 소유권 체인이 필요한 데이터베이스가 있는 경우 권장되는 방법은 **sp_configure** 를 사용하여 인스턴스에 대해 **cross db ownership chaining**옵션을 해제한 다음 ALTER DATABASE 문을 사용하여 데이터베이스 간 소유권 체인이 필요한 개별 데이터베이스에 대해 데이터베이스 간 소유권 체인을 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="13efb-115">If you have databases that require cross-database ownership chaining, the recommended practice is to turn off the **cross db ownership chaining** option for the instance using **sp_configure**; then turn on cross-database ownership chaining for individual databases that require it using the ALTER DATABASE statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13efb-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="13efb-116">See Also</span></span>  
 <span data-ttu-id="13efb-117">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="13efb-117">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="13efb-118">[CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="13efb-118">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="13efb-119">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="13efb-119">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="13efb-120">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="13efb-120">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="13efb-121">RECONFIGURE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="13efb-121">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
