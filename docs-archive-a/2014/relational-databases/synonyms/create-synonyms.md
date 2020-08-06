---
title: 동의어 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- sql12.swb.synonym.general.f1
helpviewer_keywords:
- creating synonyms
- synonyms [SQL Server], creating
ms.assetid: fedfa7a5-d0b6-4e2b-90f4-a08122958e33
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3dc18c9d0d6048c4190ba56725dd332f2dfb629e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638612"
---
# <a name="create-synonyms"></a><span data-ttu-id="06def-102">동의어 만들기</span><span class="sxs-lookup"><span data-stu-id="06def-102">Create Synonyms</span></span>
  <span data-ttu-id="06def-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 동의어를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="06def-103">This topic describes how to create a synonym in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="06def-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="06def-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="06def-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="06def-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="06def-106">보안</span><span class="sxs-lookup"><span data-stu-id="06def-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="06def-107">**다음을 사용하여 동의어 만들기**</span><span class="sxs-lookup"><span data-stu-id="06def-107">**To create a synonym, using:**</span></span>  
  
     [<span data-ttu-id="06def-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="06def-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="06def-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="06def-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="06def-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="06def-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="06def-111">보안</span><span class="sxs-lookup"><span data-stu-id="06def-111">Security</span></span>  
 <span data-ttu-id="06def-112">지정된 스키마에서 동의어를 만들려면 사용자에게 CREATE SYNONYM 권한이 있어야 하며 스키마를 소유하거나 ALTER SCHEMA 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06def-112">To create a synonym in a given schema, a user must have CREATE SYNONYM permission and either own the schema or have ALTER SCHEMA permission.</span></span> <span data-ttu-id="06def-113">CREATE SYNONYM 권한은 부여할 수 있는 권한입니다.</span><span class="sxs-lookup"><span data-stu-id="06def-113">The CREATE SYNONYM permission is a grantable permission.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="06def-114">권한</span><span class="sxs-lookup"><span data-stu-id="06def-114">Permissions</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="06def-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="06def-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-synonym"></a><span data-ttu-id="06def-116">동의어를 만들려면</span><span class="sxs-lookup"><span data-stu-id="06def-116">To Create a Synonym</span></span>  
  
1.  <span data-ttu-id="06def-117">**개체 탐색기**에서 새 뷰를 만들 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="06def-117">In **Object Explorer**, expand the database where you want to create your new view.</span></span>  
  
2.  <span data-ttu-id="06def-118">**동의어** 폴더를 마우스 오른쪽 단추로 클릭한 다음, **새 동의어...** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="06def-118">Right-click the **Synonyms** folder, then click **New Synonym...**.</span></span>  
  
3.  <span data-ttu-id="06def-119">**새 동의어 추가** 대화 상자에 다음 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="06def-119">In the **Add Synonym** dialog box, enter the following information.</span></span>  
  
     <span data-ttu-id="06def-120">**동의어 이름**</span><span class="sxs-lookup"><span data-stu-id="06def-120">**Synonym name**</span></span>  
     <span data-ttu-id="06def-121">이 개체에 사용할 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="06def-121">Type the new name you will use for this object.</span></span>  
  
     <span data-ttu-id="06def-122">**동의어 스키마**</span><span class="sxs-lookup"><span data-stu-id="06def-122">**Synonym schema**</span></span>  
     <span data-ttu-id="06def-123">이 개체에 사용할 새 이름의 스키마를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="06def-123">Type the schema of the new name you will use for this object.</span></span>  
  
     <span data-ttu-id="06def-124">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="06def-124">**Server name**</span></span>  
     <span data-ttu-id="06def-125">연결할 서버 인스턴스를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="06def-125">Type the server instance to connect to.</span></span>  
  
     <span data-ttu-id="06def-126">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="06def-126">**Database name**</span></span>  
     <span data-ttu-id="06def-127">개체가 포함된 데이터베이스를 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="06def-127">Type or select the database containing the object.</span></span>  
  
     <span data-ttu-id="06def-128">**스키마**</span><span class="sxs-lookup"><span data-stu-id="06def-128">**Schema**</span></span>  
     <span data-ttu-id="06def-129">개체를 소유하는 스키마를 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="06def-129">Type or select the schema that owns the object.</span></span>  
  
     <span data-ttu-id="06def-130">**개체 유형**</span><span class="sxs-lookup"><span data-stu-id="06def-130">**Object type**</span></span>  
     <span data-ttu-id="06def-131">개체 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="06def-131">Select the type of object.</span></span>  
  
     <span data-ttu-id="06def-132">**개체 이름**</span><span class="sxs-lookup"><span data-stu-id="06def-132">**Object name**</span></span>  
     <span data-ttu-id="06def-133">동의어가 나타내는 개체의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="06def-133">Type the name of the object to which the synonym refers.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="06def-134">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="06def-134">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-synonym"></a><span data-ttu-id="06def-135">동의어를 만들려면</span><span class="sxs-lookup"><span data-stu-id="06def-135">To Create a Synonym</span></span>  
  
1.  <span data-ttu-id="06def-136">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="06def-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="06def-137">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="06def-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="06def-138">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="06def-138">Copy and paste the following examples into the query window and click **Execute**.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="06def-139">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="06def-139">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="06def-140">다음 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에 있는 기존 테이블의 동의어를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="06def-140">The following example creates a synonym for an existing table in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="06def-141">그런 다음 이후 예에서 이 동의어가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="06def-141">The synonym is then used in subsequent examples.</span></span>  
  
```  
USE tempdb;  
GO  
CREATE SYNONYM MyAddressType  
FOR AdventureWorks2012.Person.AddressType;  
GO  
```  
  
 <span data-ttu-id="06def-142">다음 예에서는 `MyAddressType` 동의어가 참조하는 기본 테이블에 행을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="06def-142">The following example inserts a row into the base table that is referenced by the `MyAddressType` synonym.</span></span>  
  
```  
USE tempdb;  
GO  
INSERT INTO MyAddressType (Name)  
VALUES ('Test');  
GO  
```  
  
 <span data-ttu-id="06def-143">다음 예에서는 동적 SQL에서 동의어를 참조하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="06def-143">The following example demonstrates how a synonym can be referenced in dynamic SQL.</span></span>  
  
```  
USE tempdb;  
GO  
EXECUTE ('SELECT Name FROM MyAddressType');  
GO  
```  
  
  
