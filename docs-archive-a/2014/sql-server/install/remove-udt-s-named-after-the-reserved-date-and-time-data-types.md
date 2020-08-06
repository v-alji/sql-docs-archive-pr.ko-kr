---
title: 예약 된 날짜 및 시간 데이터 형식 다음에 명명 된 UDT&#39;제거 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- time data type [SQL Server], UDTs
- date data type [SQL Server], UDTs
ms.assetid: 48f109af-b1d1-4f03-a7e3-8a0b05ed94e8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 827f060b309a7a620fd448554b074f45d78d3cb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653141"
---
# <a name="remove-udt39s-named-after-the-reserved-date-and-time-data-types"></a><span data-ttu-id="080e5-102">예약 된 날짜 및 시간 데이터 형식에 해당 하는 UDT&#39;s를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="080e5-102">Remove UDT&#39;s named after the reserved DATE and TIME data types</span></span>
  <span data-ttu-id="080e5-103">업그레이드 관리자가 `date` 또는 `time` 데이터 형식용으로 예약된 용어를 따서 명명된 UDT(사용자 정의 형식)를 발견했습니다.</span><span class="sxs-lookup"><span data-stu-id="080e5-103">Upgrade Advisor detected a user-defined type (UDT) that is named after a term reserved for either the `date` or the `time` data types.</span></span>  
  
## <a name="component"></a><span data-ttu-id="080e5-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="080e5-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="080e5-105">Description</span><span class="sxs-lookup"><span data-stu-id="080e5-105">Description</span></span>  
 <span data-ttu-id="080e5-106">데이터 형식에 사용되는 용어는 CLR(공용 언어 런타임) 또는 별칭 UDT의 이름으로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="080e5-106">The terms used for data types should not be used as names for either common language runtime (CLR) or alias UDTs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="080e5-107">수정 동작</span><span class="sxs-lookup"><span data-stu-id="080e5-107">Corrective Action</span></span>  
 <span data-ttu-id="080e5-108">데이터 형식의 이름을 따서 명명된 UDT를 제거하고 예약되지 않은 이름을 사용하여 UDT를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="080e5-108">Remove the UDT that is named after the data type and recreate the UDT with an unreserved name.</span></span>  
  
  
