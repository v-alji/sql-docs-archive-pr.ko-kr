---
title: 비지속형 계산 열에서 전체 텍스트 인덱스는 허용 되지 않습니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: cba737f7-b187-47d0-8458-23dc18d18aca
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: de153d45e2f652bfea6e9dce68428af84be68b6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661509"
---
# <a name="full-text-indexes-on-nonpersisted-computed-columns-are-not-allowed"></a><span data-ttu-id="4c90c-102">비지속형 계산 열에 전체 텍스트 인덱스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4c90c-102">Full-text indexes on nonpersisted, computed columns are not allowed</span></span>
  <span data-ttu-id="4c90c-103">비결정적이고 정확하지 않은 계산 열에서는 전체 텍스트 인덱스를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4c90c-103">You cannot create full-text indexes on nondeterministic and imprecise computed columns.</span></span> <span data-ttu-id="4c90c-104">이러한 열은 유형 열 또는 전체 텍스트 키 열로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4c90c-104">Such columns cannot be used as type columns or as full-text key columns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4c90c-105">Description</span><span class="sxs-lookup"><span data-stu-id="4c90c-105">Description</span></span>  
 <span data-ttu-id="4c90c-106">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서는 비결정적이고 정확하지 않은 계산 열을 유형 열이나 전체 텍스트 키 열로 사용하여 전체 텍스트 인덱스를 만들 수 있었지만</span><span class="sxs-lookup"><span data-stu-id="4c90c-106">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], a full-text index can be created by using a nondeterministic and imprecise computed column as the type column or the full-text key column.</span></span> <span data-ttu-id="4c90c-107">이제는 이 기능이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4c90c-107">This functionality is not supported.</span></span> <span data-ttu-id="4c90c-108">업그레이드하면 오래되고 호환되지 않으며 지원되지 않는 전체 텍스트 인덱스가 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c90c-108">When you upgrade, older, incompatible, and unsupported full-text indexes are disabled.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="4c90c-109">수정 동작</span><span class="sxs-lookup"><span data-stu-id="4c90c-109">Corrective Action</span></span>  
 <span data-ttu-id="4c90c-110">전체 텍스트 인덱스를 활성화하려면 열 정의를 수정하여 열을 결정적이고 정확하게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4c90c-110">To enable these full-text indexes, modify the column definitions so that the columns are deterministic and precise.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c90c-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4c90c-111">See Also</span></span>  
 [<span data-ttu-id="4c90c-112">업그레이드 관리자 작업</span><span class="sxs-lookup"><span data-stu-id="4c90c-112">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
