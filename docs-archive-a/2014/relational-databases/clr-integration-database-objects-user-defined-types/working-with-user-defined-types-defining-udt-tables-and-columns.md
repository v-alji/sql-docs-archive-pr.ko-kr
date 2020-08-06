---
title: UDT 테이블 및 열 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [CLR integration], columns
- UDTs [CLR integration], columns
- columns [CLR integration]
- user-defined types [CLR integration], tables
- tables [CLR integration]
- UDTs [CLR integration], tables
- UDTs [CLR integration], indexes
- user-defined types [CLR integration], indexes
- indexes [CLR integration]
ms.assetid: aea495f4-ce26-4952-b019-38f012625f3f
author: rothja
ms.author: jroth
ms.openlocfilehash: aa9596629ed8b4877b1793fa0c56956c52989499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661678"
---
# <a name="defining-udt-tables-and-columns"></a><span data-ttu-id="f5268-102">UDT 테이블 및 열 정의</span><span class="sxs-lookup"><span data-stu-id="f5268-102">Defining UDT Tables and Columns</span></span>
  <span data-ttu-id="f5268-103">UDT (사용자 정의 형식) 정의를 포함 하는 어셈블리를 데이터베이스에 등록 한 후에 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 열 정의에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5268-103">Once the assembly containing the user-defined type (UDT) definition has been registered in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, it can be used in a column definition.</span></span>  
  
## <a name="creating-tables-with-udts"></a><span data-ttu-id="f5268-104">UDT를 사용하여 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="f5268-104">Creating Tables with UDTs</span></span>  
 <span data-ttu-id="f5268-105">테이블에 UDT 열을 만드는 데 사용하는 특별한 구문은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f5268-105">There is no special syntax for creating a UDT column in a table.</span></span> <span data-ttu-id="f5268-106">UDT 이름을 기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식처럼 열 정의에 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5268-106">You can use the name of the UDT in a column definition as though it were one of the intrinsic [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="f5268-107">다음 CREATE TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 id 열로 정의 된 **id** 라는 열이 있는 **Points**라는 테이블을 만들고 `int` 테이블의 기본 키로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5268-107">The following CREATE TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)] statement creates a table named **Points**, with a column named **ID,** which is defined as an `int` identity column and \ the primary key for the table.</span></span> <span data-ttu-id="f5268-108">두 번째 열은 데이터 형식이 **Point**인 **pointvalue**로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5268-108">The second column is named **PointValue**, with a data type of **Point**.</span></span> <span data-ttu-id="f5268-109">이 예에 사용 된 스키마 이름은 **dbo**입니다.</span><span class="sxs-lookup"><span data-stu-id="f5268-109">The schema name used in this example is **dbo**.</span></span> <span data-ttu-id="f5268-110">스키마 이름을 지정하려면 필요한 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5268-110">Note that you must have the necessary permissions to specify a schema name.</span></span> <span data-ttu-id="f5268-111">스키마 이름을 생략하면 데이터베이스 사용자에 대한 기본 스키마가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5268-111">If you omit the schema name, the default schema for the database user is used.</span></span>  
  
```  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a><span data-ttu-id="f5268-112">UDT 열에 대한 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="f5268-112">Creating Indexes on UDT Columns</span></span>  
 <span data-ttu-id="f5268-113">UDT 열에 대한 인덱스를 만들 수 있는 옵션은 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5268-113">There are two options for indexing a UDT column:</span></span>  
  
-   <span data-ttu-id="f5268-114">전체 값을 인덱싱합니다.</span><span class="sxs-lookup"><span data-stu-id="f5268-114">Index the full value.</span></span> <span data-ttu-id="f5268-115">이 경우 UDT가 이진 순서로 정렬되어 있으면 CREATE INDEX [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용하여 전체 UDT 열에 대해 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5268-115">In this case, if the UDT is binary ordered, you can create an index over the entire UDT column by using the CREATE INDEX [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
-   <span data-ttu-id="f5268-116">UDT 식을 인덱싱합니다.</span><span class="sxs-lookup"><span data-stu-id="f5268-116">Index UDT expressions.</span></span> <span data-ttu-id="f5268-117">UDT 식을 통해 지속형 계산 열에 대한 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5268-117">You can create indexes on persisted computed columns over UDT expressions.</span></span> <span data-ttu-id="f5268-118">UDT 식은 UDT의 속성, 메서드 또는 필드일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5268-118">The UDT expression can be a field, method, or property of a UDT.</span></span> <span data-ttu-id="f5268-119">식은 결정적이어야 하고 데이터 액세스를 수행하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5268-119">The expression must be deterministic and must not perform data access.</span></span>  
  
 <span data-ttu-id="f5268-120">자세한 내용은 [CLR 사용자 정의 형식](clr-user-defined-types.md) 및 [CREATE INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/create-index-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f5268-120">For more information, see [CLR User-Defined Types](clr-user-defined-types.md) and [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5268-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f5268-121">See Also</span></span>  
 [<span data-ttu-id="f5268-122">SQL Server의 사용자 정의 형식 작업</span><span class="sxs-lookup"><span data-stu-id="f5268-122">Working with User-Defined Types in SQL Server</span></span>](working-with-user-defined-types-in-sql-server.md)  
  
  
