---
title: HumanResources.myTeam 예제 테이블(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- myTeam sample table [SQL Server]
- bulk importing [SQL Server], examples
- bulk exporting [SQL Server], examples
ms.assetid: 27da45a0-c1f4-4bf4-ab24-6196e80d3834
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7d4e0cbbf42c2bdd25e3dd7c9577e4d0ec44549a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653379"
---
# <a name="humanresourcesmyteam-sample-table-sql-server"></a><span data-ttu-id="eeb6a-102">HumanResources.myTeam 예제 테이블(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="eeb6a-102">HumanResources.myTeam Sample Table (SQL Server)</span></span>
  <span data-ttu-id="eeb6a-103">[대량 데이터 가져오기 및 내보내기](bulk-import-and-export-of-data-sql-server.md) 의 코드 예제에는 **myTeam**이라는 특별한 용도의 테스트 테이블이 필요한 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="eeb6a-103">Many of the code examples in [Importing and Exporting Bulk Data](bulk-import-and-export-of-data-sql-server.md) require a special-purpose test table named **myTeam**.</span></span> <span data-ttu-id="eeb6a-104">예제를 실행하기 전에 **데이터베이스의** HumanResources **스키마에서** myTeam [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 테이블을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eeb6a-104">Before you can run the examples, you must create the **myTeam** table in the **HumanResources** schema of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] <span data-ttu-id="eeb6a-105">는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 샘플 데이터베이스 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="eeb6a-105">is one of the sample databases in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="eeb6a-106">**myTeam** 테이블에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eeb6a-106">The **myTeam** table is contains the following columns.</span></span>  
  
|<span data-ttu-id="eeb6a-107">열</span><span class="sxs-lookup"><span data-stu-id="eeb6a-107">Column</span></span>|<span data-ttu-id="eeb6a-108">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="eeb6a-108">Data type</span></span>|<span data-ttu-id="eeb6a-109">Null 허용 여부</span><span class="sxs-lookup"><span data-stu-id="eeb6a-109">Nullability</span></span>|<span data-ttu-id="eeb6a-110">Description</span><span class="sxs-lookup"><span data-stu-id="eeb6a-110">Description</span></span>|  
|------------|---------------|-----------------|-----------------|  
|<span data-ttu-id="eeb6a-111">**EmployeeID**</span><span class="sxs-lookup"><span data-stu-id="eeb6a-111">**EmployeeID**</span></span>|`smallint`|<span data-ttu-id="eeb6a-112">Null이 아님</span><span class="sxs-lookup"><span data-stu-id="eeb6a-112">Not null</span></span>|<span data-ttu-id="eeb6a-113">행의 기본 키.</span><span class="sxs-lookup"><span data-stu-id="eeb6a-113">Primary key for the rows.</span></span> <span data-ttu-id="eeb6a-114">팀 멤버의 직원 ID</span><span class="sxs-lookup"><span data-stu-id="eeb6a-114">Employee ID of a member of my team.</span></span>|  
|<span data-ttu-id="eeb6a-115">**이름**</span><span class="sxs-lookup"><span data-stu-id="eeb6a-115">**Name**</span></span>|`nvarchar(50)`|<span data-ttu-id="eeb6a-116">Null이 아님</span><span class="sxs-lookup"><span data-stu-id="eeb6a-116">Not null</span></span>|<span data-ttu-id="eeb6a-117">팀 멤버의 이름</span><span class="sxs-lookup"><span data-stu-id="eeb6a-117">Name of a member of my team.</span></span>|  
|<span data-ttu-id="eeb6a-118">**제목**</span><span class="sxs-lookup"><span data-stu-id="eeb6a-118">**Title**</span></span>|`nvarchar(50)`|<span data-ttu-id="eeb6a-119">Nullable</span><span class="sxs-lookup"><span data-stu-id="eeb6a-119">Nullable</span></span>|<span data-ttu-id="eeb6a-120">팀 직원의 직함</span><span class="sxs-lookup"><span data-stu-id="eeb6a-120">Title the employee performs on my team.</span></span>|  
|<span data-ttu-id="eeb6a-121">**배경**</span><span class="sxs-lookup"><span data-stu-id="eeb6a-121">**Background**</span></span>|`nvarchar(50)`|<span data-ttu-id="eeb6a-122">Null이 아님</span><span class="sxs-lookup"><span data-stu-id="eeb6a-122">Not null</span></span>|<span data-ttu-id="eeb6a-123">행이 마지막으로 업데이트된 날짜와 시간</span><span class="sxs-lookup"><span data-stu-id="eeb6a-123">Date and time the row was last updated.</span></span> <span data-ttu-id="eeb6a-124">(기본값)</span><span class="sxs-lookup"><span data-stu-id="eeb6a-124">(Default)</span></span>|  
  
 <span data-ttu-id="eeb6a-125">**HumanResources.myTeam을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="eeb6a-125">**To create HumanResources.myTeam**</span></span>  
  
-   <span data-ttu-id="eeb6a-126">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eeb6a-126">Use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    --Create HumanResources.MyTeam:   
    USE AdventureWorks;  
    GO  
    CREATE TABLE HumanResources.myTeam   
    (EmployeeID smallint NOT NULL,  
    Name nvarchar(50) NOT NULL,  
    Title nvarchar(50) NULL,  
    Background nvarchar(50) NOT NULL DEFAULT ''  
    );  
    GO  
    ```  
  
 <span data-ttu-id="eeb6a-127">**HumanResources.myTeam을 채우려면**</span><span class="sxs-lookup"><span data-stu-id="eeb6a-127">**To populate HumanResources.myTeam**</span></span>  
  
-   <span data-ttu-id="eeb6a-128">다음 `INSERT` 문을 실행하여 테이블을 두 행으로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="eeb6a-128">Execute following `INSERT` statements to populate the table with two rows:</span></span>  
  
    ```  
    USE AdventureWorks;  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(77,'Mia Doppleganger','Administrative Assistant','Microsoft Office');  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(49,'Hirum Mollicat','I.T. Specialist','Report Writing and Data Mining');  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="eeb6a-129">이 문은 4번째 열 `Background`를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="eeb6a-129">These statements skip the fourth column, `Background`.</span></span> <span data-ttu-id="eeb6a-130">이 열에는 기본값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eeb6a-130">This has a default value.</span></span> <span data-ttu-id="eeb6a-131">이 열을 건너뛰면 이 `INSERT` 문에서 이 열을 비워 두게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eeb6a-131">Skipping this column causes this `INSERT` statement to leave this column blank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeb6a-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eeb6a-132">See Also</span></span>  
 [<span data-ttu-id="eeb6a-133">데이터 대량 가져오기 및 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eeb6a-133">Bulk Import and Export of Data &#40;SQL Server&#41;</span></span>](bulk-import-and-export-of-data-sql-server.md)  
  
  
