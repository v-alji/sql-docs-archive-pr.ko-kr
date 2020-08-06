---
title: 체크 인 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- checkins [SQL Server Management Studio]
- checking in files
- source controls [SQL Server Management Studio], checkins
ms.assetid: 293e60f3-15e3-4258-b73a-8baabe15c760
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a868aafff6d9bd389671544b5f1898e82707d933
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661289"
---
# <a name="manage-checkins"></a><span data-ttu-id="54983-102">체크 인 관리</span><span class="sxs-lookup"><span data-stu-id="54983-102">Manage Checkins</span></span>
  <span data-ttu-id="54983-103">소스 제어 파일의 변경 내용을 다른 사용자가 사용할 수 있게 하려면 해당 파일을 체크 인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54983-103">To make changes to a source-controlled file available to other users, you must check in the file.</span></span> <span data-ttu-id="54983-104">파일을 체크 인하면 작성한 버전이 소스 제어 공급자에 복사되고 파일의 최신 버전이 되며 일반적으로 적절한 사용 권한을 가진 사용자가 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54983-104">When you check in a file, the version you have created is copied to the source control provider, becomes the latest version of the file, and is generally available to users who have the appropriate permissions.</span></span>  
  
 <span data-ttu-id="54983-105">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 사용 하 여 파일을 체크 인 합니다.</span><span class="sxs-lookup"><span data-stu-id="54983-105">Use [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to check in files.</span></span> <span data-ttu-id="54983-106">소스 제어 저장소를 정기적으로 업데이트해야 하지만 또한 파일 집합에 대해 제어를 유지 관리해야 할 경우 체크 인한 파일이 체크 아웃된 상태로 유지되도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54983-106">When you need to update the source control store periodically, but also need to maintain control over a set of files, you can specify that files you check in remain checked out to you.</span></span>  
  
 <span data-ttu-id="54983-107">다음 표에서는 이 섹션에서 다루는 항목에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="54983-107">The following table describes the topics in this section.</span></span>  
  
|<span data-ttu-id="54983-108">항목</span><span class="sxs-lookup"><span data-stu-id="54983-108">Topic</span></span>|<span data-ttu-id="54983-109">Description</span><span class="sxs-lookup"><span data-stu-id="54983-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="54983-110">파일 체크 인</span><span class="sxs-lookup"><span data-stu-id="54983-110">Check In Files</span></span>](../../2014/database-engine/check-in-files.md)|<span data-ttu-id="54983-111">수정한 파일을 체크 인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="54983-111">Provides instructions on how to check in a file you have modified.</span></span>|  
|[<span data-ttu-id="54983-112">수정된 파일의 목록 보기</span><span class="sxs-lookup"><span data-stu-id="54983-112">View a List of Modified Files</span></span>](../../2014/database-engine/view-a-list-of-modified-files.md)|<span data-ttu-id="54983-113">작업이 끝났을 때 함께 체크 인할 수 있는 수정된 파일 목록을 표시하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="54983-113">Explains how to display a list of modified files that you can check in together when you are finished working.</span></span>|  
|[<span data-ttu-id="54983-114">체크 인 파일 편집</span><span class="sxs-lookup"><span data-stu-id="54983-114">Edit Checked-In Files</span></span>](../../2014/database-engine/edit-checked-in-files.md)|<span data-ttu-id="54983-115">체크 아웃하지 않는 파일을 수정할 수 있도록 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 환경을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="54983-115">Explains how to configure the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment so that you can modify files that are not checked out.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54983-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="54983-116">See Also</span></span>  
 [<span data-ttu-id="54983-117">체크 아웃 관리</span><span class="sxs-lookup"><span data-stu-id="54983-117">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
