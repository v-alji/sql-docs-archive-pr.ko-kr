---
title: 파일 공유 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- sharing files
- file sharing [SQL Server]
- version control services [SQL Server], file sharing
ms.assetid: 645f5c0a-e949-4e87-8988-85e4d6128464
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 79909fcdb09e349798edfe285475f8a898c3bf04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741220"
---
# <a name="share-files"></a><span data-ttu-id="2d19c-102">파일 공유</span><span class="sxs-lookup"><span data-stu-id="2d19c-102">Share Files</span></span>
  <span data-ttu-id="2d19c-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 사용하여 여러 원본 제어 프로젝트에서 항목을 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d19c-103">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to share items across source control projects.</span></span> <span data-ttu-id="2d19c-104">항목을 공유할 경우 항목에 대한 모든 변경 내용이 항목이 공유되는 모든 프로젝트에 반영됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d19c-104">When you share an item, any changes to the item are reflected in every project to which the item is shared.</span></span>  
  
 <span data-ttu-id="2d19c-105">항목 공유는 원본 제어 사용자에게 다음 장점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2d19c-105">Item sharing provides the following advantages to source control users:</span></span>  
  
-   <span data-ttu-id="2d19c-106">공유 항목을 사용하는 각 프로젝트가 항목의 개별 복사본을 저장할 필요가 없으므로 원본 제어 클라이언트와 서버 모두에서 디스크 공간이 절약됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d19c-106">Makes it unnecessary for each project that uses the shared item to store a separate copy of the item, conserving disk space on both the source control client and server.</span></span> <span data-ttu-id="2d19c-107">원본 제어 공급자는 공유 항목을 하나의 중앙 위치에 저장하며 해당 항목이 공유되는 모든 프로젝트는 해당 위치에 대한 포인터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="2d19c-107">The source control provider stores the shared item in one central location, and every project to which it is shared stores a pointer to that location.</span></span>  
  
-   <span data-ttu-id="2d19c-108">버전 비호환성이 방지됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d19c-108">Avoids version incompatibilities.</span></span> <span data-ttu-id="2d19c-109">항목이 공유되는 모든 프로젝트가 동일한 버전의 항목을 사용하기 때문에 각 항목의 복사본이 여러 프로젝트 내에서 독립적으로 변경될 경우에 발생하는 충돌이 방지됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d19c-109">Because every project to which the item is shared uses the same version of the item, you avoid the conflicts that arise when each copy of an item is changing independently within multiple projects.</span></span>  
  
### <a name="to-share-an-item"></a><span data-ttu-id="2d19c-110">항목을 공유하려면</span><span class="sxs-lookup"><span data-stu-id="2d19c-110">To share an item</span></span>  
  
1.  <span data-ttu-id="2d19c-111">솔루션 탐색기에서 공유 파일을 넣으려는 폴더나 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2d19c-111">In Solution Explorer, select either the folder or project in which you want to place the shared files.</span></span>  
  
2.  <span data-ttu-id="2d19c-112">**파일** 메뉴에서 **원본 제어**를 가리킨 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d19c-112">On the **File** menu, point to **Source Control**, and then click **Share**.</span></span>  
  
3.  <span data-ttu-id="2d19c-113">**공유** 대상 대화 상자에서 공유할 항목의 디렉터리 목록을 검색 하 고 해당 항목을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d19c-113">In the **Share with** dialog box, browse the directory list for the item you want to share, and click that item.</span></span>  
  
4.  <span data-ttu-id="2d19c-114">**공유**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d19c-114">Click **Share**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d19c-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d19c-115">See Also</span></span>  
 [<span data-ttu-id="2d19c-116">원본 제어 기본 사항</span><span class="sxs-lookup"><span data-stu-id="2d19c-116">Source Control Basics</span></span>](../../2014/database-engine/source-control-basics.md)  
  
  
