---
title: 데이터 정렬 및 CLR 통합 데이터 형식 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
author: rothja
ms.author: jroth
ms.openlocfilehash: 1a5b0367487aeb80355b8c5c976818e1b6c1ac04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742287"
---
# <a name="collation-and-clr-integration-data-types"></a><span data-ttu-id="131f8-102">데이터 정렬 및 CLR 통합 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="131f8-102">Collation and CLR Integration Data Types</span></span>
  <span data-ttu-id="131f8-103">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]에서는 `CompareInfo` 개체가 데이터 정렬을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="131f8-103">In the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], the `CompareInfo` object handles collations.</span></span> <span data-ttu-id="131f8-104">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 문자열 API(응용 프로그래밍 인터페이스)는 현재 스레드의 `CompareInfo` 개체와 연결된 `CultureInfo` 속성을 사용하여 문자열 비교를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="131f8-104">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] string application programming interfaces (APIs) use the `CompareInfo` property associated with the `CultureInfo` object of the current thread to perform string comparisons.</span></span> <span data-ttu-id="131f8-105">개체의 기본 설정은 `CultureInfo` [!INCLUDE[msCoName](../../includes/msconame-md.md)] 를 실행 하는 컴퓨터의 Windows 로캘 설정을 기반으로 합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="131f8-105">The default setting of the `CultureInfo` object is based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows locale setting for the computer on which [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span> <span data-ttu-id="131f8-106">`CultureInfo` 값을 비교할 때 `System.String`가 명시적으로 지정되지 않은 경우 이 설정에 따라 기본 비교 의미 체계가 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="131f8-106">This determines the default comparison semantics, if no explicit `CultureInfo` is specified, for comparisons of `System.String` values.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="131f8-107">는 데이터베이스 또는 서버 데이터 정렬에 대한 `CompareInfo` 속성을 명시적으로 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="131f8-107">does not explicitly change the `CompareInfo` property to the database or server collation.</span></span> <span data-ttu-id="131f8-108">필요한 경우 사용자가 자신의 루틴에서 적절한 `CompareInfo` 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="131f8-108">If required, users must set the appropriate `CompareInfo` property in their routines.</span></span>  
  
## <a name="parameter-collation"></a><span data-ttu-id="131f8-109">매개 변수 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="131f8-109">Parameter Collation</span></span>  
 <span data-ttu-id="131f8-110">CLR(공용 언어 런타임) 루틴을 만들 때 루틴에 바인딩된 CLR 메서드의 매개 변수가 `SQLString` 형식이면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 호출 루틴을 포함하는 데이터베이스의 기본 데이터 정렬로 매개 변수 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="131f8-110">When you create a common language runtime (CLR) routine, and a parameter of a CLR method bound to the routine is of type `SQLString`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creates an instance of the parameter with the default collation of the database containing the calling routine.</span></span> <span data-ttu-id="131f8-111">매개 변수가 `SqlType`이 아닌 경우(예: `String`이 아닌 `SQLString`) 매개 변수에 데이터베이스의 데이터 정렬 정보가 연결되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="131f8-111">If a parameter is not a `SqlType` (for example, `String` rather than `SQLString`), the collation information from the database is not associated with the parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="131f8-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="131f8-112">See Also</span></span>  
 [<span data-ttu-id="131f8-113">.NET Framework의 SQL Server 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="131f8-113">SQL Server Data Types in the .NET Framework</span></span>](sql-server-data-types-in-the-net-framework.md)  
  
  
