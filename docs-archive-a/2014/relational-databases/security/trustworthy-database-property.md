---
title: TRUSTWORTHY 데이터베이스 속성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database property
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 23391fe48037d4cd7f69aef7df6649949301a0f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730296"
---
# <a name="trustworthy-database-property"></a><span data-ttu-id="e0b81-102">TRUSTWORTHY 데이터베이스 속성</span><span class="sxs-lookup"><span data-stu-id="e0b81-102">TRUSTWORTHY Database Property</span></span>
  <span data-ttu-id="e0b81-103">TRUSTWORTHY 데이터베이스 속성은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 데이터베이스 및 그 내용을 트러스트하는지 여부를 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0b81-103">The TRUSTWORTHY database property is used to indicate whether the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trusts the database and the contents within it.</span></span> <span data-ttu-id="e0b81-104">기본적으로 이 설정은 OFF이지만 ALTER DATABASE 문을 사용하여 ON으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0b81-104">By default, this setting is OFF, but can be set to ON by using the ALTER DATABASE statement.</span></span> <span data-ttu-id="e0b81-105">예들 들어 `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`입니다.</span><span class="sxs-lookup"><span data-stu-id="e0b81-105">For example, `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e0b81-106">이 옵션을 설정하려면 **sysadmin** 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b81-106">To set this option, you must be a member of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="e0b81-107">이 속성을 사용하면 다음 개체 중 하나가 포함된 데이터베이스를 연결하여 발생할 수 있는 특정 위협을 줄여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e0b81-107">This property can be used to reduce certain threats that can exist as a result of attaching a database that contains one of the following objects:</span></span>  
  
-   <span data-ttu-id="e0b81-108">EXTERNAL_ACCESS 또는 UNSAFE 권한 설정이 포함된 악의적인 어셈블리.</span><span class="sxs-lookup"><span data-stu-id="e0b81-108">Malicious assemblies with an EXTERNAL_ACCESS or UNSAFE permission setting.</span></span> <span data-ttu-id="e0b81-109">자세한 내용은 [CLR Integration Security](../clr-integration/security/clr-integration-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0b81-109">For more information, see [CLR Integration Security](../clr-integration/security/clr-integration-security.md).</span></span>  
  
-   <span data-ttu-id="e0b81-110">고급 권한 사용자로 실행하도록 정의된 악의적인 모듈.</span><span class="sxs-lookup"><span data-stu-id="e0b81-110">Malicious modules that are defined to execute as high privileged users.</span></span> <span data-ttu-id="e0b81-111">자세한 내용은 [EXECUTE AS 절&#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0b81-111">For more information, see [EXECUTE AS Clause &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql).</span></span>  
  
 <span data-ttu-id="e0b81-112">이러한 경우 모두 특정 수준의 권한이 필요하며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 이미 연결된 데이터베이스의 컨텍스트에 사용될 때 적합한 메커니즘에 의해 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0b81-112">Both of these situations require a specific degree of privileges and are protected against by appropriate mechanisms when they are used in the context of a database that is already attached to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e0b81-113">하지만 데이터베이스가 오프라인 상태인 경우 데이터베이스 파일에 액세스할 수 있는 사용자가 자신이 선택한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 이를 연결하고 데이터베이스의 악의적인 내용을 추가할 가능성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0b81-113">However, if the database is taken offline, a user that has access to the database file can potentially attach it to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] of his or her choice and add malicious content to the database.</span></span> <span data-ttu-id="e0b81-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 데이터베이스가 분리 및 연결된 경우 데이터베이스 파일에 대한 액세스를 제한하는 데이터 및 로그 파일에 특정 사용 권한이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0b81-114">When databases are detached and attached in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], certain permissions are set on the data and log files that restrict access to the database files.</span></span>  
  
 <span data-ttu-id="e0b81-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결된 데이터베이스는 즉시 트러스트될 수 없으므로 데이터베이스가 명시적으로 신뢰할 수 있는 것으로 표시되지 않는 한 데이터베이스가 해당 범위를 벗어나는 리소스에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e0b81-115">Because a database that is attached to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be immediately trusted, the database is not allowed to access resources beyond the scope of the database until the database is explicitly marked trustworthy.</span></span> <span data-ttu-id="e0b81-116">또한 데이터베이스 외부의 리소스를 액세스하도록 디자인된 모듈과 EXTERNAL_ACCESS 또는 UNSAFE 권한이 설정된 어셈블리에는 성공적인 실행을 위한 추가 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0b81-116">Also, modules that are designed to access resources outside the database, and assemblies with either the EXTERNAL_ACCESS and UNSAFE permission setting, have additional requirements in order to run successfully.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="e0b81-117">관련 내용</span><span class="sxs-lookup"><span data-stu-id="e0b81-117">Related Content</span></span>  
 [<span data-ttu-id="e0b81-118">SQL Server 데이터베이스 엔진 및 Azure SQL Database 보안 센터</span><span class="sxs-lookup"><span data-stu-id="e0b81-118">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [<span data-ttu-id="e0b81-119">ALTER DATABASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e0b81-119">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
