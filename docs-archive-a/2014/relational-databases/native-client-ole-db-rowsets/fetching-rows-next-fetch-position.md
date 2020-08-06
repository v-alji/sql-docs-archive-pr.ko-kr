---
title: 다음 페치 위치 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
author: rothja
ms.author: jroth
ms.openlocfilehash: fcc771eef4acf603148bc4b4318e810b1bd72302
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729427"
---
# <a name="next-fetch-position"></a><span data-ttu-id="7b6f0-102">다음 인출 위치</span><span class="sxs-lookup"><span data-stu-id="7b6f0-102">Next Fetch Position</span></span>
  <span data-ttu-id="7b6f0-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 다음 인출 위치를 추적 하 여 **GetNextRows** 메서드 (건너뛴 경우, 방향 변경 또는 **findnextrow**, **Seek**또는 **RestartPosition** 메서드에 대 한 중간 호출)에 대 한 호출 시퀀스에서 행을 건너뛰거나 반복 하지 않고 전체 행 집합을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider keeps track of the next fetch position so that a sequence of calls to the **GetNextRows** method (without skips, changes of direction, or intervening calls to the **FindNextRow**, **Seek**, or **RestartPosition** methods) reads the whole rowset without skipping or repeating any row.</span></span> <span data-ttu-id="7b6f0-104">**IRowset::GetNextRows**, **IRowset::RestartPosition** 또는 **IRowsetIndex::Seek**을 호출하거나 null *pBookmark* 값을 사용해 **FindNextRow**를 호출하여 다음 인출 위치를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-104">The next fetch position is changed either by calling **IRowset::GetNextRows**, **IRowset::RestartPosition**, or **IRowsetIndex::Seek**, or by calling **FindNextRow** with a null *pBookmark* value.</span></span> <span data-ttu-id="7b6f0-105">null이 아닌 *pBookmark* 값을 사용해 **FindNextRow**를 호출하면 다음 인출 위치가 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-105">Calling **FindNextRow** with a nonnull *pBookmark* value does not affect the next fetch position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b6f0-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7b6f0-106">See Also</span></span>  
 [<span data-ttu-id="7b6f0-107">행 인출</span><span class="sxs-lookup"><span data-stu-id="7b6f0-107">Fetching Rows</span></span>](fetching-rows.md)  
  
  
