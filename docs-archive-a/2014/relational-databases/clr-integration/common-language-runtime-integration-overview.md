---
title: CLR (공용 언어 런타임) 통합 개요 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- managed code [SQL Server]
- common language runtime [SQL Server], about CLR integration
- cross-language integration
- integrating CLR [SQL Server]
- .NET Framework [SQL Server], common language runtime
- code access security [CLR integration]
- managed code [SQL Server], CLR integration
ms.assetid: 7be9e644-36a2-48fc-9206-faf59fdff4d7
author: rothja
ms.author: jroth
ms.openlocfilehash: 25345fd39fb8a77f62e4e352b75629a98cb9d7af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650116"
---
# <a name="common-language-runtime-clr-integration-overview"></a><span data-ttu-id="7879d-102">CLR(공용 언어 런타임) 통합 개요</span><span class="sxs-lookup"><span data-stu-id="7879d-102">Common Language Runtime (CLR) Integration Overview</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="7879d-103">는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이제에 대 한 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET FRAMEWORK의 CLR (공용 언어 런타임) 구성 요소를 통합 하는 기능을 제공 합니다. Windows.</span><span class="sxs-lookup"><span data-stu-id="7879d-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] now features the integration of the common language runtime (CLR) component of the .NET Framework for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows.</span></span> <span data-ttu-id="7879d-104">CLR은 관리 코드에 언어 간 통합, 코드 액세스 보안, 개체 수명 관리 및 디버깅과 프로파일링 지원 등의 서비스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-104">The CLR supplies managed code with services such as cross-language integration, code access security, object lifetime management, and debugging and profiling support.</span></span> <span data-ttu-id="7879d-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 사용자 및 애플리케이션 개발자는 이제 통합된 CLR을 사용하여 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET 및 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#을 포함한 .NET Framework 언어로 저장 프로시저, 트리거, 사용자 정의 형식, 사용자 정의 함수(스칼라 및 테이블 반환), 사용자 정의 집계 함수를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-105">For [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] users and application developers, CLR integration means that you can now write stored procedures, triggers, user-defined types, user-defined functions (scalar and table-valued), and user-defined aggregate functions using any .NET Framework language, including [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="7879d-106">에는 .NET Framework 버전 4가 미리 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-106">includes the .NET Framework version 4 pre-installed.</span></span>  
  
 <span data-ttu-id="7879d-107">이 통합의 주요 이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-107">Among the major benefits of this integration are:</span></span>  
  
-   <span data-ttu-id="7879d-108">**개선된 프로그래밍 모델.**</span><span class="sxs-lookup"><span data-stu-id="7879d-108">**A better programming model.**</span></span> <span data-ttu-id="7879d-109">.NET Framework 언어는 여러 측면에서 Transact-SQL보다 기능이 풍부하며 이전에는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 개발자에게 제공되지 않던 구문 및 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-109">The .NET Framework languages are in many respects richer than Transact-SQL, offering constructs and capabilities previously not available to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] developers.</span></span> <span data-ttu-id="7879d-110">개발자는 또한 광범위한 클래스 집합을 제공하는 .NET Framework 라이브러리의 강력한 기능을 활용하여 프로그래밍 문제를 신속하고, 효율적으로 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-110">Developers may also leverage the power of the .NET Framework Library, which provides an extensive set of classes that can be used to quickly and efficiently solve programming problems.</span></span>  
  
-   <span data-ttu-id="7879d-111">**개선된 안전성 및 보안.**</span><span class="sxs-lookup"><span data-stu-id="7879d-111">**Improved safety and security.**</span></span> <span data-ttu-id="7879d-112">관리 코드는 데이터베이스 엔진에 의해 호스팅되는 공용 언어 런타임 환경에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-112">Managed code runs in a common language run-time environment, hosted by the Database Engine.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="7879d-113">는 이를 활용하여 이전 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 사용되던 확장 저장 프로시저보다 안전성 및 보안이 우수한 대안을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-113">leverages this to provide a safer and more secure alternative to the extended stored procedures available in earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="7879d-114">**데이터 형식 및 집계 함수를 정의하는 기능.**</span><span class="sxs-lookup"><span data-stu-id="7879d-114">**Ability to define data types and aggregate functions.**</span></span> <span data-ttu-id="7879d-115">사용자 정의 형식과 사용자 정의 집계는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 스토리지 및 쿼리 기능을 확장하는 새로운 관리되는 데이터베이스 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-115">User defined types and user defined aggregates are two new managed database objects which expand the storage and querying capabilities of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="7879d-116">**표준화된 환경을 통한 효율적인 개발.**</span><span class="sxs-lookup"><span data-stu-id="7879d-116">**Streamlined development through a standardized environment.**</span></span> <span data-ttu-id="7879d-117">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio .NET 개발 환경의 후속 릴리스에 데이터베이스 개발이 통합되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-117">Database development is integrated into future releases of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio .NET development environment.</span></span> <span data-ttu-id="7879d-118">개발자는 중간 계층 또는 클라이언트 계층 .NET Framework 구성 요소와 서비스를 작성할 때 사용하는 도구와 똑같은 도구를 사용하여 데이터베이스 개체와 스크립트를 개발하고 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-118">Developers use the same tools for developing and debugging database objects and scripts as they use to write middle-tier or client-tier .NET Framework components and services.</span></span>  
  
-   <span data-ttu-id="7879d-119">**성능 및 확장성 개선 가능성.**</span><span class="sxs-lookup"><span data-stu-id="7879d-119">**Potential for improved performance and scalability.**</span></span> <span data-ttu-id="7879d-120">.NET Framework 언어 컴파일 및 실행 모델은 일반적으로 Transact-SQL보다 개선된 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-120">In many situations, the .NET Framework language compilation and execution models deliver improved performance over Transact-SQL.</span></span>  
  
 <span data-ttu-id="7879d-121">다음 표에서는 이 섹션에서 다루는 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-121">This following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="7879d-122">CLR 통합 개요</span><span class="sxs-lookup"><span data-stu-id="7879d-122">Overview of CLR Integration</span></span>](clr-integration-overview.md)  
 <span data-ttu-id="7879d-123">통합된 CLR을 사용하여 작성할 수 있는 개체 유형과 데이터베이스 개체를 작성하기 위한 요구 사항을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-123">Describes the kinds of objects that can be built using CLR integration, and reviews the requirements for building database objects using CLR integration.</span></span>  
  
 [<span data-ttu-id="7879d-124">CLR 통합의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="7879d-124">What's New in CLR Integration</span></span>](clr-integration-what-s-new.md)  
 <span data-ttu-id="7879d-125">이 릴리스의 새로운 기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-125">Describes the new features in this release.</span></span>  
  
 [<span data-ttu-id="7879d-126">CLR 통합 아키텍처</span><span class="sxs-lookup"><span data-stu-id="7879d-126">Architecture of CLR Integration</span></span>](../../database-engine/dev-guide/architecture-of-clr-integration.md)  
 <span data-ttu-id="7879d-127">통합된 CLR의 디자인 목표를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-127">Describes the design goals of CLR integration.</span></span>  
  
 [<span data-ttu-id="7879d-128">CLR 통합 사용</span><span class="sxs-lookup"><span data-stu-id="7879d-128">Enabling CLR Integration</span></span>](clr-integration-enabling.md)  
 <span data-ttu-id="7879d-129">통합된 CLR을 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7879d-129">Describes how to enable CLR integration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7879d-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7879d-130">See Also</span></span>  
 <span data-ttu-id="7879d-131">[.NET Framework 설치](https://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx) </span><span class="sxs-lookup"><span data-stu-id="7879d-131">[Installing the .NET Framework](https://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx) </span></span>  
 [<span data-ttu-id="7879d-132">통합된 CLR의 성능</span><span class="sxs-lookup"><span data-stu-id="7879d-132">Performance of CLR Integration</span></span>](clr-integration-architecture-performance.md)  
  
  
