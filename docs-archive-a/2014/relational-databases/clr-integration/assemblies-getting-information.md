---
title: 어셈블리에 대 한 정보 가져오기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], metadata
- status information [SQL Server], assemblies
- metadata [SQL Server], assemblies
ms.assetid: 6aa7f18e-baad-4481-9777-8c3b230b392f
author: rothja
ms.author: jroth
ms.openlocfilehash: ec559ba5ccbb53dd92f3a5e1175a10a59fbaf43c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735356"
---
# <a name="getting-information-about-assemblies"></a><span data-ttu-id="d9259-102">어셈블리에 대한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="d9259-102">Getting Information About Assemblies</span></span>
  <span data-ttu-id="d9259-103">다음 카탈로그 뷰와 함수에서 어셈블리에 대한 메타데이터를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9259-103">The following catalog views and functions can be queried for metadata about assemblies.</span></span>  
  
 <span data-ttu-id="d9259-104">**개별 어셈블리에 대한 정보를 가져오려면**</span><span class="sxs-lookup"><span data-stu-id="d9259-104">**To get information about individual assemblies**</span></span>  
  
-   [<span data-ttu-id="d9259-105">ASSEMBLYPROPERTY &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="d9259-105">ASSEMBLYPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/assemblyproperty-transact-sql)  
  
 <span data-ttu-id="d9259-106">**데이터베이스에 있는 모든 어셈블리에 대한 정보를 가져오려면**</span><span class="sxs-lookup"><span data-stu-id="d9259-106">**To get information about all assemblies in the database**</span></span>  
  
-   [<span data-ttu-id="d9259-107">sys. Transact-sql &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="d9259-107">sys.assemblies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assemblies-transact-sql)  
  
 <span data-ttu-id="d9259-108">**어셈블리 이진 파일, 원본 파일 및 디버그 파일을 비롯한 어셈블리 파일에 대한 정보를 가져오려면**</span><span class="sxs-lookup"><span data-stu-id="d9259-108">**To get information about assembly files, including assembly binaries, source files, and debug files**</span></span>  
  
-   [<span data-ttu-id="d9259-109">assembly_files &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="d9259-109">sys.assembly_files &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-files-transact-sql)  
  
 <span data-ttu-id="d9259-110">**어셈블리 간 참조에 대한 정보를 가져오려면**</span><span class="sxs-lookup"><span data-stu-id="d9259-110">**To get information about cross-assembly references**</span></span>  
  
-   [<span data-ttu-id="d9259-111">assembly_references &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="d9259-111">sys.assembly_references &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-references-transact-sql)  
  
 <span data-ttu-id="d9259-112">**사용자 정의 유형에 대한 어셈블리 정보를 가져오려면**</span><span class="sxs-lookup"><span data-stu-id="d9259-112">**To get assembly information about user-defined types**</span></span>  
  
-   [<span data-ttu-id="d9259-113">assembly_types &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="d9259-113">sys.assembly_types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-types-transact-sql)  
  
-   [<span data-ttu-id="d9259-114">sys.types&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d9259-114">sys.types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-types-transact-sql)  
  
 <span data-ttu-id="d9259-115">**CLR(공용 언어 런타임) 저장 프로시저, 트리거 및 함수에 대한 어셈블리 정보를 가져오려면**</span><span class="sxs-lookup"><span data-stu-id="d9259-115">**To get assembly information about common language runtime (CLR) stored procedures, triggers, and functions**</span></span>  
  
-   [<span data-ttu-id="d9259-116">sys.assembly_modules&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d9259-116">sys.assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)  
  
 <span data-ttu-id="d9259-117">**비-CLR 개체에 대한 정보를 가져오려면**</span><span class="sxs-lookup"><span data-stu-id="d9259-117">**To get information about non-CLR objects**</span></span>  
  
-   [<span data-ttu-id="d9259-118">sys.sql_modules&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d9259-118">sys.sql_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="d9259-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d9259-119">See Also</span></span>  
 <span data-ttu-id="d9259-120">[어셈블리 &#40;데이터베이스 엔진&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="d9259-120">[Assemblies &#40;Database Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span></span>  
 <span data-ttu-id="d9259-121">[어셈블리 디자인](../../relational-databases/clr-integration/assemblies-designing.md) </span><span class="sxs-lookup"><span data-stu-id="d9259-121">[Designing Assemblies](../../relational-databases/clr-integration/assemblies-designing.md) </span></span>  
 [<span data-ttu-id="d9259-122">어셈블리 구현</span><span class="sxs-lookup"><span data-stu-id="d9259-122">Implementing Assemblies</span></span>](assemblies-implementing.md)  
  
  
