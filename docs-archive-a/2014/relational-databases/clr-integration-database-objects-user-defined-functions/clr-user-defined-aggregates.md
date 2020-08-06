---
title: CLR 사용자 정의 집계 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
author: rothja
ms.author: jroth
ms.openlocfilehash: d1ef5d07fe082d0eeb2c3484d6e99572d8fc80e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651729"
---
# <a name="clr-user-defined-aggregates"></a><span data-ttu-id="35e80-102">CLR 사용자 정의 집계</span><span class="sxs-lookup"><span data-stu-id="35e80-102">CLR User-Defined Aggregates</span></span>
  <span data-ttu-id="35e80-103">집계 함수는 값 집합에서 계산을 수행하고 단일 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="35e80-103">Aggregate functions perform a calculation on a set of values and return a single value.</span></span> <span data-ttu-id="35e80-104">일반적으로에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `SUM` `MAX` 입력 스칼라 값 집합에 대해 작동 하 고 해당 집합에서 단일 집계 값을 생성 하는 또는와 같은 기본 제공 집계 함수만 지원 했습니다.</span><span class="sxs-lookup"><span data-stu-id="35e80-104">Traditionally, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has supported only built-in aggregate functions, such as `SUM` or `MAX`, that operate on a set of input scalar values and generate a single aggregate value from that set.</span></span> <span data-ttu-id="35e80-105">이제 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework CLR(공용 언어 런타임)의 통합을 통해 개발자는 관리 코드로 사용자 지정 집계 함수를 만들어 [!INCLUDE[tsql](../../includes/tsql-md.md)]이나 다른 관리 코드에서 이러한 함수에 액세스할 수 있게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35e80-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] integration with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework common language runtime (CLR) now allows developers to create custom aggregate functions in managed code, and to make these functions accessible to [!INCLUDE[tsql](../../includes/tsql-md.md)] or other managed code.</span></span>  
  
 <span data-ttu-id="35e80-106">다음 표에서는 이 섹션에서 다루는 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="35e80-106">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="35e80-107">CLR 사용자 정의 집계 요구 사항</span><span class="sxs-lookup"><span data-stu-id="35e80-107">Requirements for CLR User-Defined Aggregates</span></span>](clr-user-defined-aggregates-requirements.md)  
 <span data-ttu-id="35e80-108">CLR 사용자 정의 집계 함수를 구현하기 위한 요구 사항에 대해 간략히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="35e80-108">Provides an overview of the requirements for implementing CLR user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="35e80-109">CLR 사용자 정의 집계 함수 호출</span><span class="sxs-lookup"><span data-stu-id="35e80-109">Invoking CLR User-Defined Aggregate Functions</span></span>](clr-user-defined-aggregate-invoking-functions.md)  
 <span data-ttu-id="35e80-110">사용자 정의 집계를 호출하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="35e80-110">Explains how to invoke user-defined aggregates.</span></span>  
  
  
