---
title: CLR (공용 언어 런타임) 통합 프로그래밍 개념 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- CLR [SQL Server] See common language runtime [SQL Server]
- Database Engine [SQL Server], .NET Framework
- .NET Framework [SQL Server], Database Engine programming
- common language runtime [SQL Server]
- .NET Framework [SQL Server]
ms.assetid: 951bf851-3e6e-4361-ae6a-2bcd5b837ebd
author: rothja
ms.author: jroth
ms.openlocfilehash: 38323b0145132ad60d59c001d5147a7d19942462
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649583"
---
# <a name="common-language-runtime-clr-integration-programming-concepts"></a><span data-ttu-id="1ffad-102">CLR(공용 언어 런타임) 통합 프로그래밍 개요</span><span class="sxs-lookup"><span data-stu-id="1ffad-102">Common Language Runtime (CLR) Integration Programming Concepts</span></span>
  <span data-ttu-id="1ffad-103">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]부터 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 통합된 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows용 .NET Framework의 CLR(공용 언어 런타임) 구성 요소를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-103">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features the integration of the common language runtime (CLR) component of the .NET Framework for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows.</span></span> <span data-ttu-id="1ffad-104">이를 통해 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET 및 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#을 포함한 모든 .NET Framework 언어를 사용하여 저장 프로시저, 트리거, 사용자 정의 형식, 사용자 정의 함수, 사용자 정의 집계 및 스트리밍 테이블 반환 함수를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-104">This means that you can now write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span>  
  
 <span data-ttu-id="1ffad-105">The Microsoft.SqlServer.Server 네임스페이스에는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 CLR 프로그래밍에 대한 핵심 기능이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-105">The Microsoft.SqlServer.Server namespace includes core functionality for CLR programming in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1ffad-106">그러나 Microsoft.SqlServer.Server 네임스페이스는 .NET Framework SDK에 설명되어 있는데,</span><span class="sxs-lookup"><span data-stu-id="1ffad-106">However, the Microsoft.SqlServer.Server namespace is documented in the .NET Framework SDK.</span></span> <span data-ttu-id="1ffad-107">이 설명서는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 온라인 설명서에 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-107">This documentation is not included in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1ffad-108">기본적으로 .NET Framework는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]를 설치하면 자동으로 설치되지만 .NET Framework SDK는 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-108">By default, the .NET Framework is installed with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], but the .NET Framework SDK is not.</span></span> <span data-ttu-id="1ffad-109">컴퓨터에 SDK가 설치되지 않아 온라인 설명서 컬렉션이 포함되어 있지 않을 경우 이 섹션의 SDK 내용에 대한 링크가 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-109">Without the SDK installed on your computer and included in the Books Online collection, links to SDK content in this section do not work.</span></span> <span data-ttu-id="1ffad-110">따라서 .NET Framework SDK를 설치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-110">Install the .NET Framework SDK.</span></span> <span data-ttu-id="1ffad-111">설치 되 면 [.NET FRAMEWORK Sdk 설치](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)의 지침에 따라 온라인 설명서 컬렉션과 목차에 sdk를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-111">Once installed, add the SDK to the Books Online collection and table of contents by following the instructions in [Installing the .NET Framework SDK](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx).</span></span>  
  
 <span data-ttu-id="1ffad-112">다음 표에서는 이 섹션에서 다루는 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-112">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="1ffad-113">공용 언어 런타임 &#40;CLR&#41; 통합 개요</span><span class="sxs-lookup"><span data-stu-id="1ffad-113">Common Language Runtime &#40;CLR&#41; Integration Overview</span></span>](common-language-runtime-integration-overview.md)  
 <span data-ttu-id="1ffad-114">CLR에 대한 간략한 개요를 제공하고 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 이 기술을 사용하는 방법과 그 이유에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-114">Provides a brief overview of the CLR, and describes how and why this technology has been used in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1ffad-115">또한 CLR을 사용하여 데이터베이스 개체를 만들 경우의 이점에 대해서도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-115">Describes the benefits of using the CLR to create database objects.</span></span>  
  
 [<span data-ttu-id="1ffad-116">어셈블리&#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="1ffad-116">Assemblies &#40;Database Engine&#41;</span></span>](assemblies-database-engine.md)  
 <span data-ttu-id="1ffad-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 어셈블리를 사용하여 함수, 저장 프로시저, 트리거, 사용자 정의 집계, [!INCLUDE[msCoName](../../../includes/msconame-md.md)]로 작성되지 않고 [!INCLUDE[tsql](../../../includes/tsql-md.md)] .NET Framework CLR(공용 언어 런타임)로 호스팅되는 관리 코드 언어 중 하나로 작성된 사용자 정의 형식을 배포하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-117">Describes how assemblies are used in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to deploy functions, stored procedures, triggers, user-defined aggregates, and user-defined types that are written in one of the managed code languages hosted by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework common language runtime (CLR), and not written in [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 [<span data-ttu-id="1ffad-118">CLR&#41; 통합 &#40;공용 언어 런타임을 사용 하 여 데이터베이스 개체 빌드</span><span class="sxs-lookup"><span data-stu-id="1ffad-118">Building Database Objects with Common Language Runtime &#40;CLR&#41; Integration</span></span>](database-objects/building-database-objects-with-common-language-runtime-clr-integration.md)  
 <span data-ttu-id="1ffad-119">CLR을 사용하여 작성할 수 있는 개체 유형에 대해 설명하고 CLR 데이터베이스 개체를 작성하기 위한 요구 사항을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-119">Describes the kinds of objects that can be built using the CLR, and reviews the requirements for building CLR database objects.</span></span>  
  
 [<span data-ttu-id="1ffad-120">CLR 데이터베이스 개체에서 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="1ffad-120">Data Access from CLR Database Objects</span></span>](data-access/data-access-from-clr-database-objects.md)  
 <span data-ttu-id="1ffad-121">CLR 루틴을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 저장된 데이터에 액세스하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-121">Describes how a CLR routine can access data stored in an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="1ffad-122">CLR 통합 보안</span><span class="sxs-lookup"><span data-stu-id="1ffad-122">CLR Integration Security</span></span>](security/clr-integration-security.md)  
 <span data-ttu-id="1ffad-123">CLR 통합 보안 모델에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-123">Describes the CLR integration security model.</span></span>  
  
 [<span data-ttu-id="1ffad-124">CLR 데이터베이스 개체 디버깅</span><span class="sxs-lookup"><span data-stu-id="1ffad-124">Debugging CLR Database Objects</span></span>](debugging-clr-database-objects.md)  
 <span data-ttu-id="1ffad-125">CLR 데이터베이스 개체의 디버깅에 대한 제한 사항 및 요구 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-125">Describes limitations of and requirements for debugging CLR database objects.</span></span>  
  
 [<span data-ttu-id="1ffad-126">CLR 데이터베이스 개체 배포</span><span class="sxs-lookup"><span data-stu-id="1ffad-126">Deploying CLR Database Objects</span></span>](deploying-clr-database-objects.md)  
 <span data-ttu-id="1ffad-127">프로덕션 서버에 어셈블리를 배포하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-127">Describes deploying assemblies to production servers.</span></span>  
  
 [<span data-ttu-id="1ffad-128">CLR 통합 어셈블리 관리</span><span class="sxs-lookup"><span data-stu-id="1ffad-128">Managing CLR Integration Assemblies</span></span>](assemblies/managing-clr-integration-assemblies.md)  
 <span data-ttu-id="1ffad-129">CLR 통합 어셈블리를 만들고 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-129">Describes how to create and drop CLR integration assemblies.</span></span>  
  
 [<span data-ttu-id="1ffad-130">관리되는 데이터베이스 개체 모니터링 및 문제 해결</span><span class="sxs-lookup"><span data-stu-id="1ffad-130">Monitoring and Troubleshooting Managed Database Objects</span></span>](monitoring-and-troubleshooting-managed-database-objects.md)  
 <span data-ttu-id="1ffad-131">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 실행 중인 관리되는 데이터베이스 개체와 어셈블리를 모니터링하고 문제를 해결하는 데 사용할 수 있는 도구에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-131">Provides information about the tools that can be used to monitor and troubleshoot managed database objects and assemblies running in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="1ffad-132">공용 언어 런타임 &#40;CLR&#41; 통합에 대한 사용 시나리오 및 예제</span><span class="sxs-lookup"><span data-stu-id="1ffad-132">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
 <span data-ttu-id="1ffad-133">CLR 개체를 사용하는 사용 시나리오 및 코드 예제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffad-133">Describes usage scenarios and code samples using CLR objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ffad-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ffad-134">See Also</span></span>  
 <span data-ttu-id="1ffad-135">[어셈블리 &#40;데이터베이스 엔진&#41;](assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="1ffad-135">[Assemblies &#40;Database Engine&#41;](assemblies-database-engine.md) </span></span>  
 <span data-ttu-id="1ffad-136">[.NET Framework SDK 설치](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="1ffad-136">[Installing the .NET Framework SDK](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)</span></span>  
  
  
