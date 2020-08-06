---
title: 저장(허용되지 않음) 대화 상자 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.table.tablerecreatenosave.f1
ms.assetid: 7efda8e3-739f-4c97-a497-b8808a0acbea
author: stevestein
ms.author: sstein
ms.openlocfilehash: 19e5f848f20cf74feb3e802e931cbde3aa8d3dc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734863"
---
# <a name="save-not-permitted-dialog-box"></a><span data-ttu-id="3b06c-102">저장(허용되지 않음) 대화 상자</span><span class="sxs-lookup"><span data-stu-id="3b06c-102">Save (Not Permitted) Dialog Box</span></span>
  <span data-ttu-id="3b06c-103">**저장** (허용되지 않음) 대화 상자는 변경한 내용을 적용하려면 나열된 테이블을 삭제한 다음 다시 만들어야 하므로 변경 내용 저장이 허용되지 않음을 경고합니다.</span><span class="sxs-lookup"><span data-stu-id="3b06c-103">The **Save** (Not Permitted) dialog box warns you that saving changes is not permitted because the changes you have made require the listed tables to be dropped and re-created.</span></span>  
  
 <span data-ttu-id="3b06c-104">다음 동작을 수행하려면 테이블을 다시 만들어야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b06c-104">The following actions might require a table to be re-created:</span></span>  
  
-   <span data-ttu-id="3b06c-105">테이블의 중간에 새 열 추가</span><span class="sxs-lookup"><span data-stu-id="3b06c-105">Adding a new column to the middle of the table</span></span>  
  
-   <span data-ttu-id="3b06c-106">열 삭제</span><span class="sxs-lookup"><span data-stu-id="3b06c-106">Dropping a column</span></span>  
  
-   <span data-ttu-id="3b06c-107">열의 Null 허용 여부 변경</span><span class="sxs-lookup"><span data-stu-id="3b06c-107">Changing column nullability</span></span>  
  
-   <span data-ttu-id="3b06c-108">열의 순서 변경</span><span class="sxs-lookup"><span data-stu-id="3b06c-108">Changing the order of the columns</span></span>  
  
-   <span data-ttu-id="3b06c-109">열의 데이터 형식 변경</span><span class="sxs-lookup"><span data-stu-id="3b06c-109">Changing the data type of a column</span></span>  
  
 <span data-ttu-id="3b06c-110">이 옵션을 변경하려면 **도구** 메뉴에서 **옵션**을 클릭하고 **디자이너**를 확장한 다음 **테이블 및 데이터베이스 디자이너**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b06c-110">To change this option, on the **Tools** menu, click **Options**, expand **Designers**, and then click **Table and Database Designers**.</span></span> <span data-ttu-id="3b06c-111">**테이블을 다시 만들어야 하는 변경 내용 저장 사용 안 함** 확인란을 선택하거나 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="3b06c-111">Select or clear the **Prevent saving changes that require the table to be re-created** check box.</span></span>  
  
  
