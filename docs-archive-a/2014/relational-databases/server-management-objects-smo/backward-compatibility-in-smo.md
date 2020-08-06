---
title: SMO의 이전 버전과의 호환성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 2f986436-aaf2-4eaf-9809-df849d97d4fb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73b6f4eebccf23850ccf08ec95ccb59dbc5c6293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650913"
---
# <a name="backward-compatibility-in-smo"></a><span data-ttu-id="02937-102">SMO의 이전 버전과의 호환성</span><span class="sxs-lookup"><span data-stu-id="02937-102">Backward Compatibility in SMO</span></span>
  <span data-ttu-id="02937-103">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용하여 작성된 SMO 애플리케이션은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 SMO를 사용하여 다시 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02937-103">SMO applications that were written using previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be recompiled by using SMO in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="migrating-smo-applications"></a><span data-ttu-id="02937-104">SMO 애플리케이션 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="02937-104">Migrating SMO Applications</span></span>  
 <span data-ttu-id="02937-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전 버전의 SMO dll 참조를 제거하고 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에 제공되는 새 SMO dll에 대한 참조를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="02937-105">References to SMO dlls in older versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be removed, and references to the new SMO dlls that are provided with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] must be included.</span></span>  
  
 <span data-ttu-id="02937-106">다음은 반드시 참조해야 할 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="02937-106">Minimally, you would reference the following:</span></span>  
  
-   <span data-ttu-id="02937-107">Microsoft.SqlServer.ConnectionInfo</span><span class="sxs-lookup"><span data-stu-id="02937-107">Microsoft.SqlServer.ConnectionInfo</span></span>  
  
-   <span data-ttu-id="02937-108">Microsoft.SqlServer.Smo</span><span class="sxs-lookup"><span data-stu-id="02937-108">Microsoft.SqlServer.Smo</span></span>  
  
-   <span data-ttu-id="02937-109">Microsoft.SqlServer.Management.Sdk.Sfc</span><span class="sxs-lookup"><span data-stu-id="02937-109">Microsoft.SqlServer.Management.Sdk.Sfc</span></span>  
  
 <span data-ttu-id="02937-110">이러한 파일은 연결 클래스, SMO 유틸리티 클래스 및 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="02937-110">These files are required for connection classes, SMO utility classes, and foundation classes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="02937-111">SmoEnum.dll은 제거되었으므로 이에 대한 참조는 SMO [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 프로젝트에서 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="02937-111">SmoEnum.dll has been removed so references to it must be removed from the SMO [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] project.</span></span>  
  
 <span data-ttu-id="02937-112">네임스페이스도 변경되어 다음과 같이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02937-112">The namespaces have also changed, so you can use the following:</span></span>  
  
##### <a name="for-visual-c"></a><span data-ttu-id="02937-113">Visual C#의 경우</span><span class="sxs-lookup"><span data-stu-id="02937-113">For Visual C#</span></span>  
  
```  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
```  
  
##### <a name="for-visual-basic"></a><span data-ttu-id="02937-114">Visual Basic의 경우</span><span class="sxs-lookup"><span data-stu-id="02937-114">For Visual Basic</span></span>  
  
```  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
```  
  
 <span data-ttu-id="02937-115">코드에서 `Server.GetSqlSmoObject(Urn)`와 같은 URN 기능을 사용하는 경우 Microsoft.SqlServer.Management.Sdk.Sfc 네임스페이스에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="02937-115">If your code uses Urn functionality, such as `Server.GetSqlSmoObject(Urn)`, you must link to the Microsoft.SqlServer.Management.Sdk.Sfc namespace.</span></span>  
  
 <span data-ttu-id="02937-116">코드에서 직접 전송 개체를 사용하는 경우 Microsoft.SqlServer.Management.SmoExtended 네임스페이스에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="02937-116">If your code uses the Transfer object directly, you will have to link to the Microsoft.SqlServer.Management.SmoExtended namespace.</span></span>  
  
 <span data-ttu-id="02937-117">코드를 마이그레이션할 때 코드를 수정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02937-117">When you migrate code, you might have to modify the code.</span></span> <span data-ttu-id="02937-118">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 및 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 의 몇 가지 기능이 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 더 이상 사용되지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="02937-118">This is because several [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] features have been deprecated in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="02937-119">사용 되지 않는 기능에 대 한 자세한 내용은 온라인 설명서의 [SQL Server 2014에서 사용 되지 않는 데이터베이스 엔진 기능](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md) 을 참조 하십시오 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="02937-119">For more information about deprecated features, see [Deprecated Database Engine Features in SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md) in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Books Online.</span></span>  
  
  
