---
title: 통계 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- statistics [SQL Server], modifying
- modifying statistics
ms.assetid: b06299ca-ed52-411a-b245-45eac4628c99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6dd44da6d1a80050f37f08e49773f95af0e5a339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659880"
---
# <a name="modify-statistics"></a><span data-ttu-id="71bc5-102">통계 수정</span><span class="sxs-lookup"><span data-stu-id="71bc5-102">Modify Statistics</span></span>
  <span data-ttu-id="71bc5-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 기존 통계를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71bc5-103">You can modify existing statistics in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="71bc5-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="71bc5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="71bc5-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="71bc5-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="71bc5-106">보안</span><span class="sxs-lookup"><span data-stu-id="71bc5-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="71bc5-107">**다음을 사용하여 통계를 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="71bc5-107">**To modify statistics, using:**</span></span>  
  
     [<span data-ttu-id="71bc5-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="71bc5-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="71bc5-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="71bc5-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="71bc5-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="71bc5-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="71bc5-111">보안</span><span class="sxs-lookup"><span data-stu-id="71bc5-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="71bc5-112">권한</span><span class="sxs-lookup"><span data-stu-id="71bc5-112">Permissions</span></span>  
 <span data-ttu-id="71bc5-113">다음을 만족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71bc5-113">Requires that:</span></span>  
  
-   <span data-ttu-id="71bc5-114">사용자에게 테이블이나 뷰에 대한 ALTER 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71bc5-114">The user has ALTER permission on the table or view.</span></span>  
  
-   <span data-ttu-id="71bc5-115">통계를 만들려면 테이블 또는 인덱싱된 뷰의 소유자이거나 **sysadmin** 고정 서버 역할, **db_owner** 고정 데이터베이스 역할 또는 **db_ddladmin** 고정 데이터베이스 역할 중 하나의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71bc5-115">The user be the table or indexed view owner, or a member of one of the following roles: **sysadmin** fixed server role, **db_owner** fixed database role, or the **db_ddladmin** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="71bc5-116">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="71bc5-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-statistics"></a><span data-ttu-id="71bc5-117">통계를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="71bc5-117">To modify statistics</span></span>  
  
1.  <span data-ttu-id="71bc5-118">**개체 탐색기**에서 더하기 기호를 클릭하여 통계를 수정할 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="71bc5-118">In **Object Explorer**, click the plus sign to expand the database in which you want to modify a statistic.</span></span>  
  
2.  <span data-ttu-id="71bc5-119">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="71bc5-119">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="71bc5-120">더하기 기호를 클릭하여 통계를 수정할 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="71bc5-120">Click the plus sign to expand the table in which you want to modify a statistic.</span></span>  
  
4.  <span data-ttu-id="71bc5-121">더하기 기호를 클릭하여 **통계** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="71bc5-121">Click the plus sign to expand the **Statistics** folder.</span></span>  
  
5.  <span data-ttu-id="71bc5-122">수정하려는 통계 개체를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71bc5-122">Right-click the statistics object that you wish to modify and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="71bc5-123">**통계 속성 -** *statistics_name* 대화 상자의 **일반** 페이지에서 **추가**, **제거**, **위로 이동**, **아래로 이동**을 클릭하거나 이를 조합하여 통계 속성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="71bc5-123">In the **Statistics Properties -** *statistics_name* dialog box, on the **General** page, click **Add**, **Remove**, **Move Up**, or **Move Down**, or any combination, to alter the properties of the statistics.</span></span> <span data-ttu-id="71bc5-124">**통계 열** 표 안에 있는 열의 위치는 통계의 유용성에 큰 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71bc5-124">Remember that a column's location within the **Statistics Columns** grid can substantially impact the usefulness of the statistics.</span></span>  
  
7.  <span data-ttu-id="71bc5-125">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71bc5-125">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="71bc5-126">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="71bc5-126">Using Transact-SQL</span></span>  
 <span data-ttu-id="71bc5-127">**통계를 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="71bc5-127">**To modify statistics**</span></span>  
  
 <span data-ttu-id="71bc5-128">이 작업은 Transact-SQL 문을 사용하여 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="71bc5-128">This task cannot be performed using Transact-SQL statements.</span></span> <span data-ttu-id="71bc5-129">Transact-SQL을 사용하여 통계를 수정하려면 먼저 기존 통계를 삭제하고 새로운 특성을 사용하여 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71bc5-129">To modify statistics using Transact-SQL, you must first delete the existing statistic and then re-create it with new attributes.</span></span>  
  
 <span data-ttu-id="71bc5-130">자세한 내용은 [DROP STATISTICS&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql) 및 [CREATE STATISTICS&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71bc5-130">For more information, see [DROP STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql) and [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).</span></span>  
  
  
