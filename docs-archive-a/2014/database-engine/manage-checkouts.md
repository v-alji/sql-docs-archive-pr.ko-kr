---
title: 체크 아웃 관리 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- source controls [SQL Server Management Studio], checkouts
- checkouts [SQL Server Management Studio]
- checking out files
ms.assetid: ddd4adba-d432-4005-9cb2-bb9ee3163d8e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cdfa25cdc27e707d4be705e66b215130c9d70ce1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661284"
---
# <a name="manage-checkouts"></a><span data-ttu-id="6e5d6-102">체크 아웃 관리</span><span class="sxs-lookup"><span data-stu-id="6e5d6-102">Manage Checkouts</span></span>
  <span data-ttu-id="6e5d6-103">파일이 원본 제어에 추가된 후에 파일을 수정할 수 있으려면 먼저 체크 아웃해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d6-103">After a file has been added to source control, you must check out the file before you can modify it.</span></span> <span data-ttu-id="6e5d6-104">파일을 원본 제어에서 체크 아웃할 경우 원본 제어 공급자는 로컬 디스크에서 최신 버전의 복사본을 만들고 파일의 읽기 전용 특성을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d6-104">When you check a file out of source control, the source control provider creates a copy of the latest version on your local disk and removes the read-only attribute of the file.</span></span> <span data-ttu-id="6e5d6-105">경우에 따라서는 파일을 체크 아웃하지 않고 편집해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d6-105">In some circumstances you might need to edit a file without checking out the file.</span></span> <span data-ttu-id="6e5d6-106">파일을 체크 아웃 하지 않고 파일을 편집 하는 방법에 대 한 자세한 내용은 [체크 인 파일 편집](../../2014/database-engine/edit-checked-in-files.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5d6-106">For more information about editing a file without checking the file out, see [Edit Checked-In Files](../../2014/database-engine/edit-checked-in-files.md).</span></span>  
  
 <span data-ttu-id="6e5d6-107">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 사용 하 여 파일을 수동으로 또는 자동으로 체크 아웃할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d6-107">You can use [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to check out files manually or automatically.</span></span> <span data-ttu-id="6e5d6-108">환경에 파일이 포함 된 솔루션을 열고 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] **체크 아웃** 명령을 클릭 하 여 파일을 수동으로 체크 아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d6-108">You check out files manually by opening the solution that contains the files in the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment, and then clicking the **Check Out** command.</span></span> <span data-ttu-id="6e5d6-109">자동으로 체크 아웃하도록 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 환경을 구성한 경우 파일을 자동으로 체크 아웃할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d6-109">You can check out files automatically if you configure the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment to do so.</span></span>  
  
 <span data-ttu-id="6e5d6-110">원본 제어 공급자에서 관리자가 설정한 옵션에 따라 파일을 배타적으로 또는 공유 모드로 체크 아웃할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d6-110">Depending on the options that your administrator sets on your source control provider, you can also check out files in exclusive or shared mode.</span></span> <span data-ttu-id="6e5d6-111">파일이 배타적으로 체크 아웃되면 파일을 체크 아웃한 사용자만 수정할 수 있으며 다른 사용자는 파일을 체크 아웃한 사용자가 체크 인할 때까지 파일을 체크 아웃할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d6-111">When you check out a file exclusively, only you can modify it, and no other user can check out the file until you check it in.</span></span> <span data-ttu-id="6e5d6-112">파일이 공유 모드로 체크 아웃되면 다른 모든 사용자가 동일한 파일을 체크 아웃할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d6-112">When you check out a file in shared mode, any number of users can check out the same file.</span></span> <span data-ttu-id="6e5d6-113">각 사용자가 파일을 체크 인할 경우 원본 제어 공급자는 파일을 파일의 최신 서버 버전으로 병합하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d6-113">As each user checks in the file, the source control provider attempts to merge the file with the latest server version of the file.</span></span> <span data-ttu-id="6e5d6-114">체크 인하는 버전과 최신 버전 간에 충돌이 발생하면 원본 제어 공급자는 충돌을 해결하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d6-114">If conflicts arise between the version that is being checked in and the latest version, the source control provider prompts the user to resolve the conflicts.</span></span>  
  
 <span data-ttu-id="6e5d6-115">다음 표에서는 이 섹션에서 다루는 항목에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d6-115">The following table describes the topics in this section.</span></span>  
  
|<span data-ttu-id="6e5d6-116">항목</span><span class="sxs-lookup"><span data-stu-id="6e5d6-116">Topic</span></span>|<span data-ttu-id="6e5d6-117">Description</span><span class="sxs-lookup"><span data-stu-id="6e5d6-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="6e5d6-118">파일 체크 아웃</span><span class="sxs-lookup"><span data-stu-id="6e5d6-118">Check Out Files</span></span>](../../2014/database-engine/check-out-files.md)|<span data-ttu-id="6e5d6-119">파일을 수정할 수 있도록 체크 아웃하는 방법에 대한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d6-119">Provides instructions on how to check out a file so you can modify it.</span></span>|  
|[<span data-ttu-id="6e5d6-120">체크 아웃 취소</span><span class="sxs-lookup"><span data-stu-id="6e5d6-120">Undo Checkouts</span></span>](../../2014/database-engine/undo-checkouts.md)|<span data-ttu-id="6e5d6-121">기존 체크 아웃을 취소하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d6-121">Explains how to cancel an existing checkout.</span></span>|  
|[<span data-ttu-id="6e5d6-122">편집 시 자동으로 파일 체크 아웃</span><span class="sxs-lookup"><span data-stu-id="6e5d6-122">Automatically Check Out Files Upon Edit</span></span>](../../2014/database-engine/automatically-check-out-files-upon-edit.md)|<span data-ttu-id="6e5d6-123">파일 편집을 시작할 때 파일을 체크 아웃하도록 원본 제어를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d6-123">Explains how to configure source control to check out a file when you start to edit it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e5d6-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e5d6-124">See Also</span></span>  
 <span data-ttu-id="6e5d6-125">[체크 인 관리](../../2014/database-engine/manage-checkins.md) </span><span class="sxs-lookup"><span data-stu-id="6e5d6-125">[Manage Checkins](../../2014/database-engine/manage-checkins.md) </span></span>  
 [<span data-ttu-id="6e5d6-126">체크 인 파일 편집</span><span class="sxs-lookup"><span data-stu-id="6e5d6-126">Edit Checked-In Files</span></span>](../../2014/database-engine/edit-checked-in-files.md)  
  
  
