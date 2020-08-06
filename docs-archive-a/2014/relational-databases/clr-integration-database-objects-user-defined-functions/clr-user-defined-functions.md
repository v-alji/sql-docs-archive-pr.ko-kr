---
title: CLR 사용자 정의 함수 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- building database objects [CLR integration], user-defined functions
- functions [CLR integration]
- common language runtime [SQL Server], user-defined functions
- database objects [CLR integration], user-defined functions
- user-defined functions [CLR integration]
ms.assetid: 6f7491f1-9a46-4146-ae09-056248634de2
author: rothja
ms.author: jroth
ms.openlocfilehash: ba7a4a983ec0cb36ef0fd79df44491f7f23f7648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653446"
---
# <a name="clr-user-defined-functions"></a><span data-ttu-id="40aa1-102">CLR 사용자 정의 함수</span><span class="sxs-lookup"><span data-stu-id="40aa1-102">CLR User-Defined Functions</span></span>
  <span data-ttu-id="40aa1-103">사용자 정의 함수는 매개 변수를 사용하여 계산이나 다른 동작을 수행한 다음 결과를 반환하는 루틴입니다.</span><span class="sxs-lookup"><span data-stu-id="40aa1-103">User-defined functions are routines that can take parameters, perform calculations or other actions, and return a result.</span></span> <span data-ttu-id="40aa1-104">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]부터는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET 또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#과 같은 모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 프로그래밍 언어를 사용하여 사용자 정의 함수를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40aa1-104">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], you can write user-defined functions in any [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework programming language, such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.</span></span>  
  
 <span data-ttu-id="40aa1-105">함수에는 단일 값을 반환하는 스칼라 반환 함수와 행 집합을 반환하는 테이블 반환 함수의 두 가지 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40aa1-105">There are two types of functions: scalar, which returns a single value, and table-valued, which returns a set of rows.</span></span>  
  
 <span data-ttu-id="40aa1-106">다음 표에서는 이 섹션에서 다루는 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="40aa1-106">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="40aa1-107">CLR 스칼라 반환 함수</span><span class="sxs-lookup"><span data-stu-id="40aa1-107">CLR Scalar-Valued Functions</span></span>](clr-scalar-valued-functions.md)  
 <span data-ttu-id="40aa1-108">스칼라 반환 함수의 구현 요구 사항과 예를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="40aa1-108">Covers implementation requirements and examples of scalar-valued functions.</span></span>  
  
 [<span data-ttu-id="40aa1-109">CLR 테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="40aa1-109">CLR Table-Valued Functions</span></span>](clr-table-valued-functions.md)  
 <span data-ttu-id="40aa1-110">TVF(테이블 반환 함수)를 구현하고 사용하는 방법과 [!INCLUDE[tsql](../../includes/tsql-md.md)] 및 CLR(공용 언어 런타임) TVF 간의 차이점을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="40aa1-110">Discusses how to implement and use table-valued functions (TVFs), as well as differences between [!INCLUDE[tsql](../../includes/tsql-md.md)] and common language runtime (CLR) TVFs.</span></span>  
  
 [<span data-ttu-id="40aa1-111">CLR 사용자 정의 집계</span><span class="sxs-lookup"><span data-stu-id="40aa1-111">CLR User-Defined Aggregates</span></span>](clr-user-defined-aggregates.md)  
 <span data-ttu-id="40aa1-112">사용자 정의 집계를 구현하고 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="40aa1-112">Describes how to implement and use user-defined aggregates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40aa1-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40aa1-113">See Also</span></span>  
 [<span data-ttu-id="40aa1-114">사용자 정의 함수</span><span class="sxs-lookup"><span data-stu-id="40aa1-114">User-Defined Functions</span></span>](../user-defined-functions/user-defined-functions.md)  
  
  
