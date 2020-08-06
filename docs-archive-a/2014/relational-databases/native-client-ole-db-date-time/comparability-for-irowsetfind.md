---
title: IRowsetFind 비교 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- IRowsetFind comparability [ODBC]
ms.assetid: 7d148b56-9bbe-4e55-b31f-43f115705402
author: rothja
ms.author: jroth
ms.openlocfilehash: 8ad359ca4957b434c3798d1a441eb0fd57644a59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647670"
---
# <a name="comparability-for-irowsetfind"></a><span data-ttu-id="2cd6e-102">IRowsetFind 비교</span><span class="sxs-lookup"><span data-stu-id="2cd6e-102">Comparability for IRowsetFind</span></span>
  <span data-ttu-id="2cd6e-103">IRowsetFind는 날짜/시간 형식에 대해서만 다음과 같은 비교를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd6e-103">For date/time types only, IRowsetFind supports the following comparisons:</span></span>  
  
-   <span data-ttu-id="2cd6e-104">LT</span><span class="sxs-lookup"><span data-stu-id="2cd6e-104">LT</span></span>  
  
-   <span data-ttu-id="2cd6e-105">LE</span><span class="sxs-lookup"><span data-stu-id="2cd6e-105">LE</span></span>  
  
-   <span data-ttu-id="2cd6e-106">EQ</span><span class="sxs-lookup"><span data-stu-id="2cd6e-106">EQ</span></span>  
  
-   <span data-ttu-id="2cd6e-107">GE</span><span class="sxs-lookup"><span data-stu-id="2cd6e-107">GE</span></span>  
  
-   <span data-ttu-id="2cd6e-108">GT</span><span class="sxs-lookup"><span data-stu-id="2cd6e-108">GT</span></span>  
  
-   <span data-ttu-id="2cd6e-109">NE</span><span class="sxs-lookup"><span data-stu-id="2cd6e-109">NE</span></span>  
  
-   <span data-ttu-id="2cd6e-110">IGNORE</span><span class="sxs-lookup"><span data-stu-id="2cd6e-110">IGNORE</span></span>  
  
 <span data-ttu-id="2cd6e-111">다른 비교를 시도하면 DB_E_BADCOMPAREOP가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2cd6e-111">If any other comparison is attempted, DB_E_BADCOMPAREOP is returned.</span></span> <span data-ttu-id="2cd6e-112">이것은 OLE DB 사양에 따른 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2cd6e-112">This is consistent with the OLE DB specification.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cd6e-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2cd6e-113">See Also</span></span>  
 [<span data-ttu-id="2cd6e-114">날짜 및 시간 기능 향상&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="2cd6e-114">Date and Time Improvements &#40;OLE DB&#41;</span></span>](date-and-time-improvements-ole-db.md)  
  
  
