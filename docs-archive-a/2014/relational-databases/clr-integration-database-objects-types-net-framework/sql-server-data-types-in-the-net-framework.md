---
title: .NET Framework에서 데이터 형식 SQL Server Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- System.Data library
- System.Data.SqlTypes namespace
- data types [CLR integration]
- SqlTypes library
- database objects [CLR integration], data types
- common language runtime [SQL Server], data types
- building database objects [CLR integration], data types
- mapping data types [CLR integration]
ms.assetid: c70d3ffe-2c32-45a5-849b-ef113dda09b9
author: rothja
ms.author: jroth
ms.openlocfilehash: fe0ed680e7050c58738301256575e4138f21276f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742271"
---
# <a name="sql-server-data-types-in-the-net-framework"></a><span data-ttu-id="306f1-102">.NET Framework의 SQL Server 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="306f1-102">SQL Server Data Types in the .NET Framework</span></span>
  <span data-ttu-id="306f1-103">`SqlTypes` 라이브러리는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 기본 클래스 라이브러리의 일부로,</span><span class="sxs-lookup"><span data-stu-id="306f1-103">The `SqlTypes` library is part of the base class library of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="306f1-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 포함된 데이터 형식과 의미 체계 및 전체 자릿수가 동일한 데이터 형식을 제공하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="306f1-104">It is designed to provide data types with the same semantics and precision as those found in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="306f1-105">이 항목에서는 .NET Framework 프로그래머를 대상으로 새로운 의미 체계에 대해 설명하고 `System.Data.SqlTypes` 라이브러리에 포함된 `System.Data` 네임스페이스에서 구현하는 형식을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="306f1-105">This topic describes the new semantics to .NET Framework programmers, and introduces the types implemented in the `System.Data.SqlTypes` namespace that is included in the `System.Data` library.</span></span>  
  
 <span data-ttu-id="306f1-106">다음 표에서는 이 섹션에서 다루는 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="306f1-106">This following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="306f1-107">Null 허용 여부 및 3개의 값 논리 비교</span><span class="sxs-lookup"><span data-stu-id="306f1-107">Nullability and Three-Value Logic Comparisons</span></span>](nullability-and-three-value-logic-comparisons.md)  
 <span data-ttu-id="306f1-108">CLR(공용 언어 런타임) 통합 데이터 형식에서 NULL 값이 처리되는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="306f1-108">Discusses how NULL values are handled with common language runtime (CLR) integration data types.</span></span>  
  
 [<span data-ttu-id="306f1-109">데이터 정렬 및 CLR 통합 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="306f1-109">Collation and CLR Integration Data Types</span></span>](collation-and-clr-integration-data-types.md)  
 <span data-ttu-id="306f1-110">CLR 통합에서 데이터 정렬이 처리되는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="306f1-110">Describes how collations are handled with CLR integration.</span></span>  
  
 [<span data-ttu-id="306f1-111">CLR에서 LOB&#41; 매개 변수 &#40;큰 개체 처리</span><span class="sxs-lookup"><span data-stu-id="306f1-111">Handling Large Object &#40;LOB&#41; Parameters in the CLR</span></span>](handling-large-object-lob-parameters-in-the-clr.md)  
 <span data-ttu-id="306f1-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 CLR 사이에서 LOB 형식을 전달하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="306f1-112">Describes how to pass LOB types between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the CLR.</span></span>  
  
 [<span data-ttu-id="306f1-113">CLR 매개 변수 데이터 매핑</span><span class="sxs-lookup"><span data-stu-id="306f1-113">Mapping CLR Parameter Data</span></span>](mapping-clr-parameter-data.md)  
 <span data-ttu-id="306f1-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], CLR 통합 및 .NET Framework 사이의 데이터 형식 매핑을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="306f1-114">Shows data type mappings between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], CLR integration, and the .NET Framework.</span></span>  
  
  
