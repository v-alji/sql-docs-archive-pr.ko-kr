---
title: 소스 제어에서 프로젝트 열기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], opening
- opening projects
ms.assetid: 942f93a3-e264-4ec4-ba72-a28e0509a527
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 944b121516e3782e35e213e165405b0ecceb7456
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660118"
---
# <a name="open-projects-from-source-control"></a><span data-ttu-id="ce3fa-102">원본 제어에서 프로젝트 열기</span><span class="sxs-lookup"><span data-stu-id="ce3fa-102">Open Projects from Source Control</span></span>
  <span data-ttu-id="ce3fa-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 사용하여 원본 제어에서 프로젝트를 직접 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce3fa-103">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to open projects directly from source control.</span></span> <span data-ttu-id="ce3fa-104">이렇게 할 경우 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]는 최신 버전의 프로젝트를 검색하여 로컬 디스크에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ce3fa-104">When you do this, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] retrieves the latest version of the project and copies it to your local disk.</span></span> <span data-ttu-id="ce3fa-105">또한 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 환경은 프로젝트에 대한 솔루션을 자동으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ce3fa-105">The [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment also creates a solution for the project automatically.</span></span>  
  
 <span data-ttu-id="ce3fa-106">원본 제어에서 프로젝트를 연 후에 프로젝트 파일을 체크 아웃 및 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce3fa-106">After you have opened a project from source control, you can check out and modify the project files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce3fa-107">다음 절차는 한 번만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce3fa-107">The following procedure should only be used once.</span></span> <span data-ttu-id="ce3fa-108">이후에는 **파일**, **열기**, **프로젝트**를 차례로 클릭 하 여 다른 프로젝트와 마찬가지로 프로젝트를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce3fa-108">Thereafter, you should open the project like any other project (by clicking **File**, **Open**, and then **Project**).</span></span>  
  
### <a name="to-open-a-project-from-source-control"></a><span data-ttu-id="ce3fa-109">원본 제어에서 프로젝트를 열려면</span><span class="sxs-lookup"><span data-stu-id="ce3fa-109">To open a project from source control</span></span>  
  
1.  <span data-ttu-id="ce3fa-110">**파일** 메뉴에서 **소스 제어**를 가리킨 다음 **원본 제어에서 열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce3fa-110">On the **File** menu, point to **Source Control**, and click **Open From Source Control**.</span></span>  
  
2.  <span data-ttu-id="ce3fa-111">로그온하라는 메시지가 표시되면 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe에 로그온합니다.</span><span class="sxs-lookup"><span data-stu-id="ce3fa-111">If prompted, log on to [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe.</span></span>  
  
3.  <span data-ttu-id="ce3fa-112">**SourceSafe에서 로컬 프로젝트 만들기** 대화 상자에서 열려는 프로젝트가 포함 된 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ce3fa-112">In the **Create local project from SourceSafe** dialog box, open the folder that contains the project to open.</span></span>  
  
4.  <span data-ttu-id="ce3fa-113">**폴더에 새 프로젝트 만들기** 상자는 프로젝트를 만들 로컬 디렉터리를 식별 하도록 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce3fa-113">The **Create a new project in the folder** box changes to identify the local directory in which the project will be created.</span></span> <span data-ttu-id="ce3fa-114">다른 디렉터리에 프로젝트를 배치 하려면 디렉터리에 대 한 경로를 입력 하거나 **찾아보기** 단추를 사용 하 여 로컬 디스크에서 디렉터리를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ce3fa-114">If you want to place the project in a different directory, type the path to the directory or use the **Browse** button to locate the directory on your local disk.</span></span>  
  
5.  <span data-ttu-id="ce3fa-115">**폴더에 새 프로젝트 만들기 상자**에서 올바른 폴더가 표시 되는지 확인 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce3fa-115">In the **Create a new project in the folder box**, verify that the correct folder is displayed, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="ce3fa-116">**솔루션 열기** 대화 상자에서 열고자 하는 프로젝트를 선택 하 고 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce3fa-116">In the **Open Solution** dialog box, select the project you want to open, and click **Open**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce3fa-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ce3fa-117">See Also</span></span>  
 <span data-ttu-id="ce3fa-118">[원본 제어에서 솔루션 및 프로젝트 열기](../../2014/database-engine/open-solutions-and-projects-from-source-control.md) </span><span class="sxs-lookup"><span data-stu-id="ce3fa-118">[Open Solutions and Projects from Source Control](../../2014/database-engine/open-solutions-and-projects-from-source-control.md) </span></span>  
 [<span data-ttu-id="ce3fa-119">원본 제어에서 솔루션 열기</span><span class="sxs-lookup"><span data-stu-id="ce3fa-119">Open Solutions from Source Control</span></span>](../../2014/database-engine/open-solutions-from-source-control.md)  
  
  
