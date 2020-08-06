---
title: 업그레이드 후에는 새 예약 키워드를 식별자로 사용할 수 없습니다. Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- keywords [SQL Server], after upgrade
- keywords [SQL Server], reserved
- keywords [SQL Server]
ms.assetid: cb242081-54f8-4273-a8ef-52f3751c25ef
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 36f7f8cadcba5e114feee4a3c42de6f40070ce72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650534"
---
# <a name="after-upgrade-new-reserved-keywords-cannot-be-used-as-identifiers"></a><span data-ttu-id="86100-102">업그레이드 후 새 예약 키워드는 식별자로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="86100-102">After upgrade, new reserved keywords cannot be used as identifiers</span></span>
  <span data-ttu-id="86100-103">업그레이드 관리자가 예약 키워드 사용을 감지했습니다.</span><span class="sxs-lookup"><span data-stu-id="86100-103">Upgrade Advisor detected the use of words that are reserved keywords.</span></span> <span data-ttu-id="86100-104">예약 키워드는 구분 기호로 구분하지 않는 한 식별자나 개체 이름으로 사용될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="86100-104">A reserved keyword cannot be used as an identifier or object name unless the name is delimited.</span></span>  
  
## <a name="component"></a><span data-ttu-id="86100-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="86100-105">Component</span></span>  
 <span data-ttu-id="86100-106">데이터베이스 엔진</span><span class="sxs-lookup"><span data-stu-id="86100-106">Database Engine</span></span>  
  
## <a name="description"></a><span data-ttu-id="86100-107">Description</span><span class="sxs-lookup"><span data-stu-id="86100-107">Description</span></span>  
 <span data-ttu-id="86100-108">호환성 수준 90 이하에서는 다음 단어가 예약 키워드가 아니며 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트에서 식별자나 개체 이름으로 사용될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="86100-108">At compatibility level 90 or lower, the following words are not reserved keywords and can be used as identifiers or object names in [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="86100-109">호환성 수준 100에서는 다음 단어가 완전 예약 키워드며 식별자나 개체 이름으로 사용될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="86100-109">At compatibility level 100, these words are fully reserved keywords and should not be used as identifiers or object names.</span></span>  
  
-   <span data-ttu-id="86100-110">EXTERNAL</span><span class="sxs-lookup"><span data-stu-id="86100-110">EXTERNAL</span></span>  
  
-   <span data-ttu-id="86100-111">MERGE</span><span class="sxs-lookup"><span data-stu-id="86100-111">MERGE</span></span>  
  
-   <span data-ttu-id="86100-112">PIVOT</span><span class="sxs-lookup"><span data-stu-id="86100-112">PIVOT</span></span>  
  
-   <span data-ttu-id="86100-113">REVERT</span><span class="sxs-lookup"><span data-stu-id="86100-113">REVERT</span></span>  
  
-   <span data-ttu-id="86100-114">STOPLIST</span><span class="sxs-lookup"><span data-stu-id="86100-114">STOPLIST</span></span>  
  
-   <span data-ttu-id="86100-115">TABLESAMPLE</span><span class="sxs-lookup"><span data-stu-id="86100-115">TABLESAMPLE</span></span>  
  
-   <span data-ttu-id="86100-116">UNPIVOT</span><span class="sxs-lookup"><span data-stu-id="86100-116">UNPIVOT</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="86100-117">수정 동작</span><span class="sxs-lookup"><span data-stu-id="86100-117">Corrective Action</span></span>  
 <span data-ttu-id="86100-118">개체의 이름을 바꾸는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="86100-118">We recommend that you rename the object.</span></span> <span data-ttu-id="86100-119">업그레이드하기 전에 개체의 이름을 바꿀 수 없으면 이름을 바꿀 수 있을 때까지 다음 방법 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="86100-119">If that cannot be done before upgrading, use one of the following methods until the name can be changed:</span></span>  
  
-   <span data-ttu-id="86100-120">90 이하의 데이터베이스 호환성 수준 설정을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="86100-120">Retain the database compatibility level setting of 90 or lower.</span></span>  
  
-   <span data-ttu-id="86100-121">구분 기호로 구분 식별자를 사용하여 개체를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="86100-121">Refer to the object by using delimited identifiers.</span></span> <span data-ttu-id="86100-122">예를 들어 문은 `CREATE TABLE [MERGE] ([MERGE] int);` 대괄호를 사용 하 여 개체 이름 MERGE를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="86100-122">For example, the statement `CREATE TABLE [MERGE] ([MERGE] int);` uses brackets to delimit the object name MERGE.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="86100-123">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="86100-123">External Resources</span></span>  
 [<span data-ttu-id="86100-124">예약 키워드&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="86100-124">Reserved Keywords &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reserved-keywords-transact-sql)  
  
 [<span data-ttu-id="86100-125">MERGE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="86100-125">MERGE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/merge-transact-sql)  
  
 [<span data-ttu-id="86100-126">구분 식별자(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="86100-126">Delimited Identifiers (Database Engine)</span></span>](https://go.microsoft.com/fwlink/?LinkId=112509)  
  
 [<span data-ttu-id="86100-127">ALTER DATABASE 호환성 수준&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="86100-127">ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
