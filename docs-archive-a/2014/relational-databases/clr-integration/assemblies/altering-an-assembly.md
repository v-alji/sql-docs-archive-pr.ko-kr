---
title: 어셈블리 변경 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], modifying
- permissions [CLR integration]
- altering assemblies
- ALTER ASSEMBLY statement
ms.assetid: 9e765fbd-f339-473c-8537-22f478e79696
author: rothja
ms.author: jroth
ms.openlocfilehash: c22ca979675d3b7f263e3bc6de0c41c134a1abcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735340"
---
# <a name="altering-an-assembly"></a><span data-ttu-id="a0e75-102">어셈블리 변경</span><span class="sxs-lookup"><span data-stu-id="a0e75-102">Altering an Assembly</span></span>
  <span data-ttu-id="a0e75-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 등록된 어셈블리를 ALTER ASSEMBLY 문을 사용하여 최신 버전에서 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e75-103">Assemblies that have been registered in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can be updated from a more recent version using the ALTER ASSEMBLY statement.</span></span> <span data-ttu-id="a0e75-104">어셈블리를 업데이트하려면 ALTER ASSEMBLY 문을 다음 구문과 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e75-104">To update an assembly, use the ALTER ASSEMBLY statement with the following syntax:</span></span>  
  
```  
ALTER ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
```  
  
 <span data-ttu-id="a0e75-105">ALTER ASSEMBLY는 해당 어셈블리를 사용하는 현재 실행 중인 프로세스를 중단하지 않습니다. 이러한 프로세스는 변경되지 않은 어셈블리를 사용하여 계속해서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0e75-105">ALTER ASSEMBLY does not disrupt currently running processes that are using the assembly; the processes continue executing with the unaltered assembly.</span></span> <span data-ttu-id="a0e75-106">트리거, 저장 프로시저, 집계 함수 및 CLR(공용 언어 런타임) 함수의 서명을 변경하는 데는 ALTER ASSEMBLY를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e75-106">ALTER ASSEMBLY cannot be used to change the signatures of common language runtime (CLR) functions, aggregate functions, stored procedures, and triggers.</span></span> <span data-ttu-id="a0e75-107">새 퍼블릭 메서드를 어셈블리에 추가하고 프라이빗 메서드를 수정할 수 있으며 서명이나 특성을 변경하지 않는 범위에서 퍼블릭 메서드를 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e75-107">New public methods can be added to the assembly, private methods can be modified in any way, and public methods can be modified as long as signatures or attributes are not changed.</span></span> <span data-ttu-id="a0e75-108">데이터 멤버 또는 기본 클래스를 비롯하여 기본적으로 직렬화된 사용자 정의 형식에 포함된 필드는 ALTER ASSEMBLY를 사용하여 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e75-108">Fields that are contained within a native-serialized user-defined type, including data members or base classes, cannot be changed by using ALTER ASSEMBLY.</span></span> <span data-ttu-id="a0e75-109">다른 모든 변경은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e75-109">All other changes are unsupported.</span></span> <span data-ttu-id="a0e75-110">자세한 내용은 [ALTER ASSEMBLY &#40;transact-sql&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a0e75-110">For more information, see [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql).</span></span>  
  
## <a name="changing-the-permission-set-of-an-assembly"></a><span data-ttu-id="a0e75-111">어셈블리의 권한 집합 변경</span><span class="sxs-lookup"><span data-stu-id="a0e75-111">Changing the Permission Set of an Assembly</span></span>  
 <span data-ttu-id="a0e75-112">ALTER ASSEMBLY 문을 사용하여 어셈블리의 권한 집합도 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e75-112">The permission set of an assembly can also be changed using the ALTER ASSEMBLY statement.</span></span> <span data-ttu-id="a0e75-113">다음 문은 SQLCLRTest 어셈블리의 권한 집합을 `EXTERNAL_ACCESS`로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e75-113">The following statement changes the permission set of the SQLCLRTest assembly to `EXTERNAL_ACCESS`.</span></span>  
  
```  
ALTER ASSEMBLY SQLCLRTest  
WITH PERMISSION_SET = EXTERNAL_ACCESS   
```  
  
 <span data-ttu-id="a0e75-114">어셈블리의 권한 집합을 `SAFE`에서 `EXTERNAL_ACCESS` 또는 `UNSAFE`로 변경하려면 먼저 어셈블리에 대한 `EXTERNAL ACCESS ASSEMBLY` 권한 또는 `UNSAFE ASSEMBLY` 권한이 있는 비대칭 키 및 해당 로그인을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e75-114">If the permission set of an assembly is being changed from `SAFE` to `EXTERNAL_ACCESS` or `UNSAFE`, an asymmetric key and corresponding login with `EXTERNAL ACCESS ASSEMBLY` permission or `UNSAFE ASSEMBLY` permission for the assembly must first be created.</span></span> <span data-ttu-id="a0e75-115">자세한 내용은 [Creating an Assembly](creating-an-assembly.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0e75-115">For more information, see [Creating an Assembly](creating-an-assembly.md).</span></span>  
  
## <a name="adding-the-source-code-of-an-assembly"></a><span data-ttu-id="a0e75-116">어셈블리의 원본 코드 추가</span><span class="sxs-lookup"><span data-stu-id="a0e75-116">Adding the Source Code of an Assembly</span></span>  
 <span data-ttu-id="a0e75-117">ALTER ASSEMBLY 구문의 ADD FILE 절은 CREATE ASSEMBLY에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e75-117">The ADD FILE clause in the ALTER ASSEMBLY syntax is not present in CREATE ASSEMBLY.</span></span> <span data-ttu-id="a0e75-118">이 절을 사용하여 원본 코드나 어셈블리와 연결된 다른 파일을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e75-118">You can use it to add source code or any other files associated with an assembly.</span></span> <span data-ttu-id="a0e75-119">이렇게 하면 파일이 원래 위치에서 복사되어 데이터베이스의 시스템 테이블에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0e75-119">The files are copied from their original locations and stored in system tables in the database.</span></span> <span data-ttu-id="a0e75-120">따라서 UDT의 현재 버전을 다시 만들거나 문서화해야 할 경우 간편하게 원본 코드나 기타 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e75-120">This ensures that you always have source code or other files on hand should you ever need to re-create or document the current version of the UDT.</span></span>  
  
 <span data-ttu-id="a0e75-121">다음 문은 Point UDT의 Point.cs 클래스 원본 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e75-121">The following statement adds the Point.cs class source code for the Point UDT.</span></span> <span data-ttu-id="a0e75-122">이 문은 Point.cs 파일에 있는 텍스트를 복사하여 "PointSource"라는 이름으로 데이터베이스에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e75-122">This copies the text contained in the Point.cs file and stores it in the database under the name "PointSource".</span></span>  
  
 `ALTER ASSEMBLY Point`  
  
 `ADD FILE FROM 'C:\Projects\Point\Point.cs' AS PointSource`  
  
## <a name="see-also"></a><span data-ttu-id="a0e75-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a0e75-123">See Also</span></span>  
 <span data-ttu-id="a0e75-124">[CLR 통합 어셈블리 관리](managing-clr-integration-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="a0e75-124">[Managing CLR Integration Assemblies](managing-clr-integration-assemblies.md) </span></span>  
 <span data-ttu-id="a0e75-125">[어셈블리 만들기](creating-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="a0e75-125">[Creating an Assembly](creating-an-assembly.md) </span></span>  
 <span data-ttu-id="a0e75-126">[어셈블리 삭제](dropping-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="a0e75-126">[Dropping an Assembly](dropping-an-assembly.md) </span></span>  
 [<span data-ttu-id="a0e75-127">ALTER ASSEMBLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a0e75-127">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
  
