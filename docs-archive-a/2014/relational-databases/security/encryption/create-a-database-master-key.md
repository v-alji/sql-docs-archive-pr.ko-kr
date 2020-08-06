---
title: 데이터베이스 마스터 키 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql-server-2014
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: jaszymas
ms.author: jaszymas
ms.reviewer: carlrab
ms.openlocfilehash: cb8305d9d5a3c72e6dffafd231f21110a5abdd14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741716"
---
# <a name="create-a-database-master-key"></a><span data-ttu-id="83a2d-102">데이터베이스 마스터 키 만들기</span><span class="sxs-lookup"><span data-stu-id="83a2d-102">Create a Database Master Key</span></span>

<span data-ttu-id="83a2d-103">이 항목에서는를 사용 하 여에서 데이터베이스에 데이터베이스 마스터 키를 만드는 방법에 대해 설명 `master` [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[tsql](../../../includes/tsql-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a2d-103">This topic describes how to create a database master key in the `master` database in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>

<span data-ttu-id="83a2d-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="83a2d-104">**In This Topic**</span></span>

- <span data-ttu-id="83a2d-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="83a2d-105">**Before you begin:**</span></span>

  [<span data-ttu-id="83a2d-106">보안</span><span class="sxs-lookup"><span data-stu-id="83a2d-106">Security</span></span>](#Security)

- [<span data-ttu-id="83a2d-107">Transact-SQL을 사용하여 데이터베이스 마스터 키를 만들려면</span><span class="sxs-lookup"><span data-stu-id="83a2d-107">To create a database master key using Transact-SQL</span></span>](#TsqlProcedure)

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="83a2d-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="83a2d-108">Before You Begin</span></span>

### <a name="security"></a><a name="Security"></a> <span data-ttu-id="83a2d-109">보안</span><span class="sxs-lookup"><span data-stu-id="83a2d-109">Security</span></span>

#### <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="83a2d-110">권한</span><span class="sxs-lookup"><span data-stu-id="83a2d-110">Permissions</span></span>

<span data-ttu-id="83a2d-111">데이터베이스에 대한 CONTROL 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="83a2d-111">Requires CONTROL permission on the database.</span></span>

## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="83a2d-112">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="83a2d-112">Using Transact-SQL</span></span>

### <a name="to-create-a-database-master-key"></a><span data-ttu-id="83a2d-113">데이터베이스 마스터 키를 만들려면</span><span class="sxs-lookup"><span data-stu-id="83a2d-113">To create a database master key</span></span>

1. <span data-ttu-id="83a2d-114">데이터베이스에 저장되는 마스터 키의 복사본을 암호화하기 위한 암호를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="83a2d-114">Choose a password for encrypting the copy of the master key that will be stored in the database.</span></span>
2. <span data-ttu-id="83a2d-115">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="83a2d-115">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>
3. <span data-ttu-id="83a2d-116">**시스템 데이터베이스**를 확장하고 `master`를 마우스 오른쪽 단추를 클릭한 다음, **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83a2d-116">Expand **System Databases**, right-click `master` and then click **New Query**.</span></span>
4. <span data-ttu-id="83a2d-117">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83a2d-117">Copy and paste the following example into the query window and click **Execute**.</span></span>

  ```sql
  -- Creates the master key.
  -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."
  CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';
```

<span data-ttu-id="83a2d-118">자세한 내용은 [CREATE MASTER KEY&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83a2d-118">For more information, see [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql).</span></span>
