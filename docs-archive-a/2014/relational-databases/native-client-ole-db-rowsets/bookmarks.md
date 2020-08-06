---
title: 책갈피 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- SQL Server Native Client OLE DB provider, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
ms.assetid: 7d9076f2-bf9c-452e-b816-70371a0c1644
author: rothja
ms.author: jroth
ms.openlocfilehash: be8e5486e5a442ddafa133a9cbd3f408d30a50d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738254"
---
# <a name="bookmarks"></a><span data-ttu-id="93afb-102">책갈피</span><span class="sxs-lookup"><span data-stu-id="93afb-102">Bookmarks</span></span>
  <span data-ttu-id="93afb-103">소비자는 책갈피를 사용하여 신속하게 특정 행으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93afb-103">Bookmarks let consumers quickly return to a row.</span></span> <span data-ttu-id="93afb-104">즉, 소비자는 책갈피 값을 바탕으로 행에 임의로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93afb-104">With bookmarks, consumers can access rows randomly based on the bookmark value.</span></span> <span data-ttu-id="93afb-105">책갈피 열은 행 집합의 0번 열입니다.</span><span class="sxs-lookup"><span data-stu-id="93afb-105">The bookmark column is column 0 in the rowset.</span></span> <span data-ttu-id="93afb-106">소비자는 바인딩 구조의 dwFlag 필드 값을 DBCOLUMNSINFO_ISBOOKMARK로 설정하여 해당 열이 책갈피로 사용되는 행임을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93afb-106">The consumer sets the dwFlag field value of the binding structure to DBCOLUMNSINFO_ISBOOKMARK to indicate that the column is used as a bookmark.</span></span> <span data-ttu-id="93afb-107">소비자는 또한 행 집합 속성 DBPROP_BOOKMARKS를 VARIANT_TRUE로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="93afb-107">The consumer also sets the rowset property DBPROP_BOOKMARKS to VARIANT_TRUE.</span></span> <span data-ttu-id="93afb-108">이렇게 하면 행 집합에 0번 열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93afb-108">This lets column 0 be present in the rowset.</span></span> <span data-ttu-id="93afb-109">그런 다음, **IRowsetLocate::GetRowsAt** 메서드를 사용하여 책갈피에서 오프셋으로 지정한 행부터 행을 인출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93afb-109">The **IRowsetLocate::GetRowsAt** method is then used to fetch rows, starting with the row specified as an offset from a bookmark.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93afb-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="93afb-110">See Also</span></span>  
 [<span data-ttu-id="93afb-111">행 집합</span><span class="sxs-lookup"><span data-stu-id="93afb-111">Rowsets</span></span>](rowsets.md)  
  
  
