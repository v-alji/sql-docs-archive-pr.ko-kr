---
title: 버전 정보 설정 및 검색 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- historical information [SQL Server]
- source controls [SQL Server Management Studio], version information
- retrieving version information
- current file version information
- version control services [SQL Server], retrieving version information
- version control services [SQL Server], setting version information
- status information [SQL Server], source control files
- historical information [SQL Server], source control files
ms.assetid: c3f253c4-4e3d-48e8-8d90-bd6ee899faf7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: eff3d40ba9b663ba8611508c5b9f0c9961005b81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728667"
---
# <a name="set-and-retrieve-version-information"></a><span data-ttu-id="758b5-102">버전 정보 설정 및 검색</span><span class="sxs-lookup"><span data-stu-id="758b5-102">Set and Retrieve Version Information</span></span>
  <span data-ttu-id="758b5-103">버전 정보에는 원본 제어 파일의 기록 및 현재 상태가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="758b5-103">Version information includes the history and current status of a source-controlled file.</span></span> <span data-ttu-id="758b5-104">모든 원본 제어 파일에서 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe는 포괄적인 기록을 유지 관리하므로 시간이 지남에 따라 하나 이상의 파일이 발전하는 상황을 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="758b5-104">For every source-controlled file, [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe maintains a comprehensive history, so you can track the evolution of one or more files over time.</span></span> <span data-ttu-id="758b5-105">또한 이 정보를 사용하여 모든 파일 버전의 로컬 복사본을 검색하거나 두 개의 파일 버전을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="758b5-105">You can also use this information to retrieve a local copy of any version of the file or to compare any two file versions.</span></span>  
  
 <span data-ttu-id="758b5-106">파일 기록에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="758b5-106">The history of a file includes:</span></span>  
  
-   <span data-ttu-id="758b5-107">동일한 파일의 다른 버전 간에 해당 시퀀스를 식별하는 버전 번호</span><span class="sxs-lookup"><span data-stu-id="758b5-107">The version number, which identifies its sequence among other versions of the same file.</span></span>  
  
-   <span data-ttu-id="758b5-108">실행된 동작.</span><span class="sxs-lookup"><span data-stu-id="758b5-108">The action performed.</span></span> <span data-ttu-id="758b5-109">파일 작성, 체크 인 및 삭제 작업이 추적됩니다.</span><span class="sxs-lookup"><span data-stu-id="758b5-109">Tracked operations include file creation, check in, and deletion.</span></span>  
  
-   <span data-ttu-id="758b5-110">파일과 연관된 동작을 수행한 사람의 사용자 이름</span><span class="sxs-lookup"><span data-stu-id="758b5-110">The user name of the person who performed an action involving the file.</span></span>  
  
-   <span data-ttu-id="758b5-111">작업이 수행된 날짜와 시간</span><span class="sxs-lookup"><span data-stu-id="758b5-111">The date and time when the operation was performed.</span></span>  
  
 <span data-ttu-id="758b5-112">또한 Visual SourceSafe는 현재 로드된 솔루션에 대한 현재 상태 정보를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="758b5-112">Visual SourceSafe also maintains current status information on the currently loaded solution.</span></span> <span data-ttu-id="758b5-113">이 정보는 다음을 비롯하여 현재 파일 상태에 대한 스냅샷을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="758b5-113">This information provides a snapshot of the current state of the file, including:</span></span>  
  
-   <span data-ttu-id="758b5-114">파일을 체크 아웃한 사용자의 ID</span><span class="sxs-lookup"><span data-stu-id="758b5-114">The identity of the user who has the file checked out.</span></span>  
  
-   <span data-ttu-id="758b5-115">선택한 파일의 최신 버전 번호</span><span class="sxs-lookup"><span data-stu-id="758b5-115">The latest version number of the selected file.</span></span>  
  
-   <span data-ttu-id="758b5-116">버전을 만든 날짜</span><span class="sxs-lookup"><span data-stu-id="758b5-116">The date when the version was created.</span></span>  
  
-   <span data-ttu-id="758b5-117">버전과 연관된 사용자 의견</span><span class="sxs-lookup"><span data-stu-id="758b5-117">The user comment associated with the version.</span></span>  
  
-   <span data-ttu-id="758b5-118">파일을 공유한 프로젝트의 경로</span><span class="sxs-lookup"><span data-stu-id="758b5-118">The paths to the projects with which the file is shared.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="758b5-119">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="758b5-119">In This Section</span></span>  
  
-   [<span data-ttu-id="758b5-120">파일 기록 보기</span><span class="sxs-lookup"><span data-stu-id="758b5-120">View File History</span></span>](../../2014/database-engine/view-file-history.md)  
  
-   [<span data-ttu-id="758b5-121">프로젝트 기록 보기</span><span class="sxs-lookup"><span data-stu-id="758b5-121">View Project History</span></span>](../../2014/database-engine/view-project-history.md)  
  
-   [<span data-ttu-id="758b5-122">파일 상태 보기</span><span class="sxs-lookup"><span data-stu-id="758b5-122">View File Status</span></span>](../../2014/database-engine/view-file-status.md)  
  
-   [<span data-ttu-id="758b5-123">파일 검색</span><span class="sxs-lookup"><span data-stu-id="758b5-123">Retrieve Files</span></span>](../../2014/database-engine/retrieve-files.md)  
  
-   [<span data-ttu-id="758b5-124">최신 버전으로 버전 지정</span><span class="sxs-lookup"><span data-stu-id="758b5-124">Specify a Version as the Latest Version</span></span>](../../2014/database-engine/specify-a-version-as-the-latest-version.md)  
  
-   [<span data-ttu-id="758b5-125">파일 비교</span><span class="sxs-lookup"><span data-stu-id="758b5-125">Compare Files</span></span>](../../2014/database-engine/compare-files.md)  
  
-   [<span data-ttu-id="758b5-126">파일 공유</span><span class="sxs-lookup"><span data-stu-id="758b5-126">Share Files</span></span>](../../2014/database-engine/share-files.md)  
  
-   [<span data-ttu-id="758b5-127">기록 및 상태 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="758b5-127">Create History and Status Reports</span></span>](../../2014/database-engine/create-history-and-status-reports.md)  
  
## <a name="see-also"></a><span data-ttu-id="758b5-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="758b5-128">See Also</span></span>  
 [<span data-ttu-id="758b5-129">원본 제어 기본 사항</span><span class="sxs-lookup"><span data-stu-id="758b5-129">Source Control Basics</span></span>](../../2014/database-engine/source-control-basics.md)  
  
  
