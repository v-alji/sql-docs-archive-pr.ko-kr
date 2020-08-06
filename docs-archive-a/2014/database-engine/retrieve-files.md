---
title: 파일 검색 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], file retrieval
- file retrieval [SQL Server]
- retrieving files
ms.assetid: 37b74426-e262-43b2-a81f-79b1fd1a36ec
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ebced9ea69f304344893289140687cd6d511e923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659624"
---
# <a name="retrieve-files"></a><span data-ttu-id="55f5e-102">파일 검색</span><span class="sxs-lookup"><span data-stu-id="55f5e-102">Retrieve Files</span></span>
  <span data-ttu-id="55f5e-103">소스 제어 프로젝트를 연 후에 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 사용하여 원본 제어 저장소에서 프로젝트가 상주하는 로컬 디렉터리로 프로젝트 파일의 로컬 복사본을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55f5e-103">After you have opened a source-controlled project, you can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to retrieve local copies of project files from the source control store to the local directory in which the project resides.</span></span>  
  
 <span data-ttu-id="55f5e-104">통합 소스 제어를 사용하여 다음 방법으로 파일을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55f5e-104">You can use integrated source control to retrieve files in the following ways:</span></span>  
  
-   <span data-ttu-id="55f5e-105">**최신 버전 가져오기 (하위 폴더)** 명령</span><span class="sxs-lookup"><span data-stu-id="55f5e-105">**Get Latest Version (Recursive)** command</span></span>  
  
     <span data-ttu-id="55f5e-106">선택한 파일 중에 체크 인한 최신 버전을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="55f5e-106">Retrieves the latest checked in version of the selected files.</span></span> <span data-ttu-id="55f5e-107">솔루션이나 프로젝트가 선택되면 이 명령은 모든 솔루션과 프로젝트 파일의 최신 버전을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="55f5e-107">If a solution or project is selected, this command retrieves the latest version of all solution and project files.</span></span>  
  
-   <span data-ttu-id="55f5e-108">**Get** 명령</span><span class="sxs-lookup"><span data-stu-id="55f5e-108">**Get** command</span></span>  
  
     <span data-ttu-id="55f5e-109">선택 된 파일의 최신 버전을 검색 하거나 선택한 솔루션 또는 프로젝트에서 파일의 하위 집합을 검색 하는 데 사용할 수 있는 **가져오기** 대화 상자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="55f5e-109">Displays the **Get** dialog box, which you can use to retrieve the latest version of a selected file, or to retrieve a subset of the files in the selected solution or project.</span></span>  
  
### <a name="to-retrieve-the-latest-version-of-all-the-files-in-a-project"></a><span data-ttu-id="55f5e-110">프로젝트에 있는 모든 파일의 최신 버전을 검색하려면</span><span class="sxs-lookup"><span data-stu-id="55f5e-110">To retrieve the latest version of all the files in a project</span></span>  
  
1.  <span data-ttu-id="55f5e-111">솔루션 탐색기에서 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55f5e-111">In Solution Explorer, select the project.</span></span>  
  
2.  <span data-ttu-id="55f5e-112">**파일** 메뉴에서 **원본 제어**를 가리킨 다음 **최신 버전 가져오기 (하위 폴더 포함)** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="55f5e-112">On the **File** menu, point to **Source Control**, and then click **Get Latest Version (Recursive)**.</span></span>  
  
 <span data-ttu-id="55f5e-113">프로젝트에 있는 파일의 최신 버전이 로컬 디스크의 프로젝트 위치로 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="55f5e-113">The most recent versions of the files in the project are retrieved to the project location on your local disk.</span></span>  
  
#### <a name="to-retrieve-only-certain-files-in-a-project"></a><span data-ttu-id="55f5e-114">프로젝트의 특정 파일만 검색하려면</span><span class="sxs-lookup"><span data-stu-id="55f5e-114">To retrieve only certain files in a project</span></span>  
  
1.  <span data-ttu-id="55f5e-115">솔루션 탐색기에서 검색할 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55f5e-115">In Solution Explorer, select the item you want to retrieve.</span></span>  
  
2.  <span data-ttu-id="55f5e-116">**파일** 메뉴에서 **원본 제어**를 가리킨 다음 **가져오기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="55f5e-116">On the **File** menu, point to **Source Control**, and then click **Get**.</span></span>  
  
3.  <span data-ttu-id="55f5e-117">**가져오기** 대화 상자에서 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="55f5e-117">In the **Get** dialog box, click **OK**.</span></span> <span data-ttu-id="55f5e-118">또는 솔루션 탐색기에서 솔루션이나 프로젝트를 선택한 경우 검색하지 않으려는 항목 옆에 있는 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="55f5e-118">Alternatively, if you selected a solution or project in Solution Explorer, clear the check boxes that appear next to the items you do not want to retrieve.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f5e-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="55f5e-119">See Also</span></span>  
 <span data-ttu-id="55f5e-120">[소스 제어를 &#40;대화 상자를 가져옵니다&#41;](../../2014/database-engine/get-dialog-box-source-control.md) </span><span class="sxs-lookup"><span data-stu-id="55f5e-120">[Get Dialog Box &#40;Source Control&#41;](../../2014/database-engine/get-dialog-box-source-control.md) </span></span>  
 <span data-ttu-id="55f5e-121">[버전 정보 설정 및 검색](../../2014/database-engine/set-and-retrieve-version-information.md) </span><span class="sxs-lookup"><span data-stu-id="55f5e-121">[Set and Retrieve Version Information](../../2014/database-engine/set-and-retrieve-version-information.md) </span></span>  
 <span data-ttu-id="55f5e-122">[프로젝트 기록 보기](../../2014/database-engine/view-project-history.md) </span><span class="sxs-lookup"><span data-stu-id="55f5e-122">[View Project History](../../2014/database-engine/view-project-history.md) </span></span>  
 [<span data-ttu-id="55f5e-123">파일 상태 보기</span><span class="sxs-lookup"><span data-stu-id="55f5e-123">View File Status</span></span>](../../2014/database-engine/view-file-status.md)  
  
  
