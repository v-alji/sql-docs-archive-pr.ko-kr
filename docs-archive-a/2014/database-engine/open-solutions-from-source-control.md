---
title: 소스 제어에서 솔루션 열기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- opening solutions
- solutions [SQL Server Management Studio], opening
ms.assetid: a96a1f0d-0183-4587-a3b0-4598309cbdd2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 808a4851bcc1f51690b2ba924a859bcccf9a6adb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660116"
---
# <a name="open-solutions-from-source-control"></a><span data-ttu-id="0725c-102">원본 제어에서 솔루션 열기</span><span class="sxs-lookup"><span data-stu-id="0725c-102">Open Solutions from Source Control</span></span>
  <span data-ttu-id="0725c-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 사용하여 원본 제어에서 솔루션을 직접 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0725c-103">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to open solutions directly from source control.</span></span> <span data-ttu-id="0725c-104">이렇게 할 경우 Studio 환경은 최신 버전의 솔루션 파일에 대한 복사본을 지정된 위치에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0725c-104">When you do this, the Studio environment creates a copy of the latest version of the solution files at the location you specify.</span></span>  
  
 <span data-ttu-id="0725c-105">솔루션의 로컬 복사본이 로컬 디스크에 존재하지 않을 경우 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 사용하여 솔루션을 체크 아웃하거나 솔루션 파일을 검색할 수 있으려면 먼저 원본 제어에서 프로젝트를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0725c-105">If a local copy of the solution does not exist on your local disk, you must open the project from source control before you can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to check out the solution or retrieve solution files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0725c-106">원본 제어에서 여는 솔루션의 로컬 복사본이 이미 존재할 경우 로컬 복사본을 덮어쓸 것인지 묻는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0725c-106">If you already have a local copy of the solution you are opening from source control, you are prompted to overwrite the local copy.</span></span>  
  
### <a name="to-open-a-solution-from-source-control"></a><span data-ttu-id="0725c-107">원본 제어에서 솔루션을 열려면</span><span class="sxs-lookup"><span data-stu-id="0725c-107">To open a solution from source control</span></span>  
  
1.  <span data-ttu-id="0725c-108">**파일** 메뉴에서 **소스 제어**를 가리킨 다음 **원본 제어에서 열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0725c-108">On the **File** menu, point to **Source Control**, and click **Open From Source Control**.</span></span>  
  
2.  <span data-ttu-id="0725c-109">로그온하라는 메시지가 표시되면 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe에 로그온합니다.</span><span class="sxs-lookup"><span data-stu-id="0725c-109">If prompted, log on to [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe.</span></span>  
  
3.  <span data-ttu-id="0725c-110">**SourceSafe에서 로컬 프로젝트 만들기** 대화 상자에서 열려는 솔루션을 포함 하는 폴더를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0725c-110">In the **Create local project from SourceSafe** dialog box, select the folder that contains the solution you want to open, and click **OK**.</span></span>  
  
4.  <span data-ttu-id="0725c-111">솔루션에 대 한 작업 폴더가 로컬 디스크 드라이브에 이미 있는 경우 **폴더에 새 프로젝트 만들기** 상자는 로컬 디렉터리를 식별 하도록 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0725c-111">If a working folder for the solution already exists on your local disk drive, the **Create a new project in the folder** box changes to identify the local directory.</span></span> <span data-ttu-id="0725c-112">솔루션의 작업 폴더가 존재하지 않을 경우 솔루션을 열어야 하는 로컬 디렉터리를 입력하거나 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0725c-112">If no working folder for the solution exists, you can type or browse to the local directory in which the solution should be opened.</span></span>  
  
5.  <span data-ttu-id="0725c-113">**솔루션 열기** 대화 상자에서 솔루션 파일을 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0725c-113">In the **Open Solution** dialog box, select the solution file, and click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0725c-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0725c-114">See Also</span></span>  
 [<span data-ttu-id="0725c-115">원본 제어에서 프로젝트 열기</span><span class="sxs-lookup"><span data-stu-id="0725c-115">Open Projects from Source Control</span></span>](../../2014/database-engine/open-projects-from-source-control.md)  
  
  
