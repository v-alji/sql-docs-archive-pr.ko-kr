---
title: IRow::GetColumns 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
ms.assetid: 1f5d2e03-e6fe-4ea1-b71d-55d02b5d59ae
author: rothja
ms.author: jroth
ms.openlocfilehash: f323dda790946565bc0dbd63c9e1f9d17ac7494b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648364"
---
# <a name="using-irowgetcolumns"></a><span data-ttu-id="624ca-102">IRow::GetColumns 사용</span><span class="sxs-lookup"><span data-stu-id="624ca-102">Using IRow::GetColumns</span></span>
  <span data-ttu-id="624ca-103">**IRow** 구현에서는 열에 대한 정방향 전용 순차적 액세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="624ca-103">The **IRow** implementation allows forward-only sequential access to the columns.</span></span> <span data-ttu-id="624ca-104">**IRow::GetColumns**를 한 번 호출하거나 행의 여러 열에 액세스할 때마다 **IRow::GetColumns**를 여러 번 호출하여 행의 모든 열에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="624ca-104">You can either access all the columns in the row with a single call to **IRow::GetColumns** or call **IRow::GetColumns** multiple times every time that you access several columns in the row.</span></span>  
  
 <span data-ttu-id="624ca-105">**IRow::GetColumns**를 여러 번 호출할 때 겹치지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="624ca-105">The multiple calls to **IRow::GetColumns** should not overlap.</span></span> <span data-ttu-id="624ca-106">예를 들어 **IRow::GetColumns**에 대한 첫 번째 호출에서 열 1, 2, 3을 검색하는 경우 **IRow::GetColumns**에 대한 두 번째 호출은 열 4, 5, 6에 대한 호출이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="624ca-106">For example, if the first call to **IRow::GetColumns** retrieves columns 1, 2, and 3, the second call to **IRow::GetColumns** should call for columns 4, 5, and 6.</span></span> <span data-ttu-id="624ca-107">나중에 **IRow::GetColumns**에 대한 호출이 겹치면 상태 플래그(DBCOLUMNACCESS의 dwstatus 필드)가 DBSTATUS_E_UNAVAILABLE로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="624ca-107">If later calls to **IRow::GetColumns** overlap, the status flag (dwstatus field in DBCOLUMNACCESS) is set to DBSTATUS_E_UNAVAILABLE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="624ca-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="624ca-108">See Also</span></span>  
 [<span data-ttu-id="624ca-109">IRow를 사용하여 단일 행 인출</span><span class="sxs-lookup"><span data-stu-id="624ca-109">Fetching a Single Row with IRow</span></span>](fetching-a-single-row-with-irow.md)  
  
  
