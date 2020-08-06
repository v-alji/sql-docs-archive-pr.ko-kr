---
title: MSSQLSERVER_21862 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b945350d9c7a862d4274f464afbd7fc5472f732c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731655"
---
# <a name="mssqlserver_21862"></a><span data-ttu-id="e04a0-102">MSSQLSERVER_21862</span><span class="sxs-lookup"><span data-stu-id="e04a0-102">MSSQLSERVER_21862</span></span>
    
## <a name="details"></a><span data-ttu-id="e04a0-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="e04a0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e04a0-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="e04a0-104">Product Name</span></span>|<span data-ttu-id="e04a0-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e04a0-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e04a0-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="e04a0-106">Event ID</span></span>|<span data-ttu-id="e04a0-107">21862</span><span class="sxs-lookup"><span data-stu-id="e04a0-107">21862</span></span>|  
|<span data-ttu-id="e04a0-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="e04a0-108">Event Source</span></span>|<span data-ttu-id="e04a0-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e04a0-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e04a0-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="e04a0-110">Component</span></span>|<span data-ttu-id="e04a0-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e04a0-111">SQLEngine</span></span>|  
|<span data-ttu-id="e04a0-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="e04a0-112">Symbolic Name</span></span>|<span data-ttu-id="e04a0-113">SQLErrorNum21862</span><span class="sxs-lookup"><span data-stu-id="e04a0-113">SQLErrorNum21862</span></span>|  
|<span data-ttu-id="e04a0-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="e04a0-114">Message Text</span></span>|<span data-ttu-id="e04a0-115">'database snapshot' 또는 'database snapshot character' 동기화 메서드를 사용하여 게시에 FILESTREAM 열을 게시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e04a0-115">FILESTREAM columns cannot be published in a publication by using a synchronization method of either 'database snapshot' or 'database snapshot character'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e04a0-116">설명</span><span class="sxs-lookup"><span data-stu-id="e04a0-116">Explanation</span></span>  
 <span data-ttu-id="e04a0-117">데이터베이스 스냅샷을 통해 FILESTREAM 데이터에 액세스할 수 없으므로 게시의 동기화 메서드에 대해 *database snapshot* 또는 *database_snapshot_character* 매개 변수를 지정하면 스냅샷 에이전트가 FILESTREAM 데이터를 읽을 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e04a0-117">Because FILESTREAM data cannot be accessed through a database snapshot, the snapshot agent will be unable to read FILESTREAM data when either the *database snapshot* or *database_snapshot_character* parameter is specified for the synchronization method of the publication.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e04a0-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="e04a0-118">User Action</span></span>  
 <span data-ttu-id="e04a0-119">게시 동기화 메서드를 *database snapshot* 또는 *database_snapshot_character*가 아닌 다른 것으로 변경하거나 게시에서 FILESTREAM 열을 제외하세요.</span><span class="sxs-lookup"><span data-stu-id="e04a0-119">Change the publication synchronization method to something other than *database snapshot* or *database_snapshot_character*, or just exclude the FILESTREAM column from the publication.</span></span>  
  
  
