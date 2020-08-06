---
title: 저장 프로시저 정의 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services]
- OLAP [Analysis Services], stored procedures
- external routines [Analysis Services]
- stored procedures [Analysis Services], about stored procedures
ms.assetid: f9c57d91-f60f-4f0e-8f7f-d87f4ba97b7c
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc1f028f822d2289ee79702feb2494487040977c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732159"
---
# <a name="defining-stored-procedures"></a><span data-ttu-id="9c1db-102">저장 프로시저 정의</span><span class="sxs-lookup"><span data-stu-id="9c1db-102">Defining Stored Procedures</span></span>
  <span data-ttu-id="9c1db-103">저장 프로시저를 사용 하 여에서 외부 루틴을 호출할 수 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9c1db-103">You can use stored procedures to call external routines from [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="9c1db-104">저장 프로시저에서 호출할 외부 루틴을 C, C++, C#, Visual Basic 또는 Visual Basic .NET과 같은 CLR(공용 언어 런타임) 언어로 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c1db-104">You can write an external routines called by a stored procedure in any common language runtime (CLR) language, such as C, C++, C#, Visual Basic, or Visual Basic .NET.</span></span> <span data-ttu-id="9c1db-105">저장 프로시저는 한 번 만든 다음 다른 저장 프로시저, 계산 측정값 또는 클라이언트 애플리케이션과 같은 다양한 컨텍스트에서 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c1db-105">A stored procedure can be created once and called from many contexts, such as other stored procedures, calculated measures, or client applications.</span></span> <span data-ttu-id="9c1db-106">저장 프로시저를 사용하면 공통 코드를 한 번 개발한 다음 단일 위치에 저장하여 재사용할 수 있으므로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 개발 및 구현이 간편해집니다.</span><span class="sxs-lookup"><span data-stu-id="9c1db-106">Stored procedures simplify [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database development and implementation by allowing common code to be developed once and stored in a single location.</span></span> <span data-ttu-id="9c1db-107">또한 MDX의 기본 기능에서 제공하지 않는 비즈니스 기능을 애플리케이션에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c1db-107">Stored procedures can be used to add business functionality to your applications that is not provided by the native functionality of MDX.</span></span>  
  
 <span data-ttu-id="9c1db-108">이 섹션에서는 저장 프로시저를 이해하고 디자인하고 구현하는 데 필요한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9c1db-108">This section provides the information necessary to understand, design, and implement stored procedures.</span></span>  
  
|<span data-ttu-id="9c1db-109">항목</span><span class="sxs-lookup"><span data-stu-id="9c1db-109">Topic</span></span>|<span data-ttu-id="9c1db-110">Description</span><span class="sxs-lookup"><span data-stu-id="9c1db-110">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="9c1db-111">저장 프로시저 디자인</span><span class="sxs-lookup"><span data-stu-id="9c1db-111">Designing Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/designing-stored-procedures.md)|<span data-ttu-id="9c1db-112">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 사용할 어셈블리를 디자인하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9c1db-112">Describes how to design assemblies for use with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="9c1db-113">저장 프로시저 만들기</span><span class="sxs-lookup"><span data-stu-id="9c1db-113">Creating Stored Procedures</span></span>](creating-stored-procedures.md)|<span data-ttu-id="9c1db-114">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 어셈블리를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9c1db-114">Describes how to create assemblies for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="9c1db-115">저장 프로시저 호출</span><span class="sxs-lookup"><span data-stu-id="9c1db-115">Calling Stored Procedures</span></span>](calling-stored-procedures.md)|<span data-ttu-id="9c1db-116">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 어셈블리를 사용하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9c1db-116">Provides information on how to use assemblies in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="9c1db-117">저장 프로시저의 쿼리 컨텍스트 액세스</span><span class="sxs-lookup"><span data-stu-id="9c1db-117">Accessing Query Context in Stored Procedures</span></span>](accessing-query-context-in-stored-procedures.md)|<span data-ttu-id="9c1db-118">어셈블리를 사용하여 범위 및 컨텍스트 정보에 액세스하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9c1db-118">Describes how to access scope and context information with assemblies.</span></span>|  
|[<span data-ttu-id="9c1db-119">저장 프로시저의 보안 설정</span><span class="sxs-lookup"><span data-stu-id="9c1db-119">Setting Security for Stored Procedures</span></span>](setting-security-for-stored-procedures.md)|<span data-ttu-id="9c1db-120">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 어셈블리의 보안을 구성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9c1db-120">Describes how to configure security for assemblies in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="9c1db-121">저장 프로시저 디버깅</span><span class="sxs-lookup"><span data-stu-id="9c1db-121">Debugging Stored Procedures</span></span>](debugging-stored-procedures.md)|<span data-ttu-id="9c1db-122">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 어셈블리를 디버깅하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9c1db-122">Describes how to debug assemblies in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c1db-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9c1db-123">See Also</span></span>  
 [<span data-ttu-id="9c1db-124">다차원 모델 어셈블리 관리</span><span class="sxs-lookup"><span data-stu-id="9c1db-124">Multidimensional Model Assemblies Management</span></span>](../multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
