---
title: 수정된 기능(포함된 데이터베이스) | Microsoft 문서
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- contained database, modifications to DBs
ms.assetid: a2942509-39a2-4903-b504-ae80a300a9de
author: stevestein
ms.author: sstein
ms.openlocfilehash: bc52821deeb879022881f838c61823b23c0c10c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742159"
---
# <a name="modified-features-contained-database"></a><span data-ttu-id="fdda9-102">수정된 기능(포함된 데이터베이스)</span><span class="sxs-lookup"><span data-stu-id="fdda9-102">Modified Features (Contained Database)</span></span>
  <span data-ttu-id="fdda9-103">다음 기능은 부분적으로 포함된 데이터베이스에서 지원하도록 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fdda9-103">The following features have been modified to be supported by a partially contained database.</span></span> <span data-ttu-id="fdda9-104">일반적으로 기능은 데이터베이스 경계를 넘지 않도록 수정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdda9-104">Features are usually modified so they do not cross the database boundary.</span></span>  
  
 <span data-ttu-id="fdda9-105">자세한 내용은 [Contained Databases](contained-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fdda9-105">For more information, see [Contained Databases](contained-databases.md).</span></span>  
  
## <a name="alter-database"></a><span data-ttu-id="fdda9-106">ALTER DATABASE</span><span class="sxs-lookup"><span data-stu-id="fdda9-106">ALTER DATABASE</span></span>  
  
### <a name="application-level"></a><span data-ttu-id="fdda9-107">애플리케이션 수준</span><span class="sxs-lookup"><span data-stu-id="fdda9-107">Application Level</span></span>  
 <span data-ttu-id="fdda9-108">포함된 데이터베이스 내부에서 ALTER DATABASE 문을 사용하는 경우 구문은 포함되지 않은 데이터베이스에 사용되는 구문과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="fdda9-108">When using the ALTER DATABASE statement from inside of a contained database, the syntax differs from that used for a non-contained database.</span></span> <span data-ttu-id="fdda9-109">이러한 차이에는 데이터베이스를 넘어 인스턴스로 확장되는 문 요소의 제한 사항이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdda9-109">This difference includes restrictions of elements of the statement that extend beyond the database to the instance.</span></span> <span data-ttu-id="fdda9-110">자세한 내용은 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fdda9-110">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
### <a name="instance-level"></a><span data-ttu-id="fdda9-111">인스턴스 수준</span><span class="sxs-lookup"><span data-stu-id="fdda9-111">Instance Level</span></span>  
 <span data-ttu-id="fdda9-112">포함된 데이터베이스 외부에서 사용되는 ALTER DATABASE의 구문은 포함되지 않은 데이터베이스에 사용될 때의 구문과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="fdda9-112">The syntax for the ALTER DATABASE when used outside of a contained database differs from that used for non-contained databases.</span></span> <span data-ttu-id="fdda9-113">이러한 변경 사항은 데이터베이스 경계를 넘는 문제를 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="fdda9-113">These changes prevent crossing the database boundary.</span></span> <span data-ttu-id="fdda9-114">자세한 내용은 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fdda9-114">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="create-database"></a><span data-ttu-id="fdda9-115">CREATE DATABASE</span><span class="sxs-lookup"><span data-stu-id="fdda9-115">CREATE DATABASE</span></span>  
 <span data-ttu-id="fdda9-116">포함된 데이터베이스에 대한 CREATE DATABASE 구문은 포함되지 않은 데이터베이스에 대한 CREATE DATABASE 구문과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="fdda9-116">The CREATE DATABASE syntax for a contained database differs from that for a non-contained database.</span></span> <span data-ttu-id="fdda9-117">새 구문 요구 사항 및 허용 사항에 대한 자세한 내용은 [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fdda9-117">See [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)for information about new syntax requirements and allowances.</span></span>  
  
## <a name="temporary-tables"></a><span data-ttu-id="fdda9-118">임시 테이블</span><span class="sxs-lookup"><span data-stu-id="fdda9-118">Temporary Tables</span></span>  
 <span data-ttu-id="fdda9-119">로컬 임시 테이블은 포함된 데이터베이스 내에 허용되지만 해당 동작은 포함되지 않은 데이터베이스에서의 동작과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="fdda9-119">Local temporary tables are permitted within a contained database, but their behavior differs from those in non-contained databases.</span></span> <span data-ttu-id="fdda9-120">포함되지 않은 데이터베이스에서 임시 테이블 데이터는 **tempdb**의 데이터 정렬에서 데이터 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdda9-120">In non-contained databases, temporary table data is collated in the collation of **tempdb**.</span></span> <span data-ttu-id="fdda9-121">포함된 데이터베이스에서 임시 테이블 데이터는 포함된 데이터베이스의 데이터 정렬에서 데이터 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdda9-121">In a contained database temporary table data is collated in the collation of the contained database.</span></span>  
  
 <span data-ttu-id="fdda9-122">임시 테이블과 연결된 모든 메타데이터(예: 테이블 및 열 이름, 인덱스 등)는 카탈로그 데이터 정렬에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdda9-122">All metadata associated with temporary tables (for example, table and column names, indexes, and so on) will be in the catalog collation.</span></span>  
  
 <span data-ttu-id="fdda9-123">명명된 제약 조건은 임시 테이블에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fdda9-123">Named constraints may not be used in temporary tables.</span></span>  
  
 <span data-ttu-id="fdda9-124">임시 테이블은 사용자 정의 형식, XML 스키마 컬렉션 또는 사용자 정의 함수를 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fdda9-124">Temporary tables may not refer to user-defined types, XML schema collections, or user-defined functions.</span></span>  
  
## <a name="collation"></a><span data-ttu-id="fdda9-125">데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="fdda9-125">Collation</span></span>  
 <span data-ttu-id="fdda9-126">포함되지 않은 데이터베이스 모델에는 데이터베이스 데이터 정렬, 인스턴스 데이터 정렬 및 tempdb 데이터 정렬이라는 별도의 세 가지 데이터 정렬이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdda9-126">In the non-contained database model, there are three separate types of collation: Database collation, Instance collation, and tempdb collation.</span></span> <span data-ttu-id="fdda9-127">포함된 데이터베이스는 두 가지의 데이터 정렬인 데이터베이스 데이터 정렬과 새 카탈로그 데이터 정렬만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fdda9-127">Contained databases use only two collations, database collation and the new catalog collation.</span></span> <span data-ttu-id="fdda9-128">포함된 데이터베이스 데이터 정렬에 대한 자세한 내용은 [Contained Database Collations](contained-database-collations.md) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fdda9-128">See [Contained Database Collations](contained-database-collations.md) for more details on contained database collation.</span></span>  
  
## <a name="user-options"></a><span data-ttu-id="fdda9-129">사용자 옵션</span><span class="sxs-lookup"><span data-stu-id="fdda9-129">User Options</span></span>  
 <span data-ttu-id="fdda9-130">포함된 데이터베이스를 사용하도록 설정할 경우 [인스턴스에 대해](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md) user options 옵션 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]을 0으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdda9-130">When enabling contained databases, the [user options Option](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md) must be set to 0 for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdda9-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fdda9-131">See Also</span></span>  
 <span data-ttu-id="fdda9-132">[포함된 데이터베이스 데이터 정렬](contained-database-collations.md) </span><span class="sxs-lookup"><span data-stu-id="fdda9-132">[Contained Database Collations](contained-database-collations.md) </span></span>  
 [<span data-ttu-id="fdda9-133">포함된 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="fdda9-133">Contained Databases</span></span>](contained-databases.md)  
  
  
