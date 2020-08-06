---
title: 예약 된 ORDPATH 데이터 형식 다음에 명명 된 UDT&#39;제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 474e910a-6abb-4e28-acc2-055338c011d4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0528d19de17781d863e3a42fdef7db558fe5d190
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742803"
---
# <a name="remove-udt39s-named-after-the-reserved-ordpath-data-type"></a><span data-ttu-id="58874-102">예약 된 ORDPATH 데이터 형식 다음에 명명 된 UDT&#39;제거</span><span class="sxs-lookup"><span data-stu-id="58874-102">Remove UDT&#39;s named after the reserved ORDPATH data type</span></span>
  <span data-ttu-id="58874-103">업그레이드 관리자가 `ORDPATH` 데이터 형식용으로 예약된 용어를 따서 명명된 UDT(사용자 정의 형식)를 발견했습니다.</span><span class="sxs-lookup"><span data-stu-id="58874-103">Upgrade Advisor detected a user-defined type (UDT) that is named after a term reserved for the `ORDPATH` data type.</span></span>  
  
## <a name="component"></a><span data-ttu-id="58874-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="58874-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="58874-105">설명</span><span class="sxs-lookup"><span data-stu-id="58874-105">Description</span></span>  
 <span data-ttu-id="58874-106">기본 제공 데이터 형식에 사용되는 용어는 CLR(공용 언어 런타임) 또는 별칭 UDT의 이름으로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="58874-106">The terms used for built-in data types should not be used as names for either common language runtime (CLR) or alias UDTs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="58874-107">수정 동작</span><span class="sxs-lookup"><span data-stu-id="58874-107">Corrective Action</span></span>  
 <span data-ttu-id="58874-108">데이터 형식의 이름을 따서 명명된 UDT를 제거하고 예약되지 않은 이름을 사용하여 UDT를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="58874-108">Remove the UDT that is named after the data type and recreate the UDT with an unreserved name.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="58874-109">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="58874-109">External Resources</span></span>  
 [<span data-ttu-id="58874-110">사용자 정의 형식 만들기</span><span class="sxs-lookup"><span data-stu-id="58874-110">Creating a User-Defined Type</span></span>](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
