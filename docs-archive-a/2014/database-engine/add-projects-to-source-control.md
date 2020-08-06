---
title: 소스 제어에 프로젝트 추가 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- projects [SQL Server Management Studio], adding
ms.assetid: fd4616b2-a564-4a66-ac53-d1f5cba213c2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0afef4ef91e4d80db7e956d03a95a2ecffe1dc4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647840"
---
# <a name="add-projects-to-source-control"></a><span data-ttu-id="eae75-102">원본 제어에 프로젝트 추가</span><span class="sxs-lookup"><span data-stu-id="eae75-102">Add Projects to Source Control</span></span>
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="eae75-103">솔루션은 여러 스크립트 프로젝트를 호스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae75-103">solutions can host multiple script projects.</span></span> <span data-ttu-id="eae75-104">프로젝트를 원본 제어에 추가하는 방법은 프로젝트가 속하는 솔루션이 원본 제어에서 사용 중인지 여부에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="eae75-104">How you add a project to source control depends upon whether the solution to which the project belongs is under source control.</span></span> <span data-ttu-id="eae75-105">솔루션이 원본 제어에서 사용 중일 경우 솔루션을 체크 인하면 프로젝트가 원본 제어에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="eae75-105">If the solution is under source control, checking in the solution automatically adds the project to source control.</span></span> <span data-ttu-id="eae75-106">솔루션 체크 인에 대 한 자세한 내용은 [파일 체크](../../2014/database-engine/check-in-files.md)인을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="eae75-106">For more information about checking in solutions, see [Check In Files](../../2014/database-engine/check-in-files.md).</span></span>  
  
 <span data-ttu-id="eae75-107">이 프로젝트가 속하는 솔루션이 원본 제어에서 사용 중이 아니면 해당 솔루션을 원본 제어에 추가할 수 있습니다. 이렇게 하면 솔루션의 프로젝트가 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="eae75-107">If the solution that this project belongs to is not under source control, you can add that solution to source control, which then automatically adds the solution's projects.</span></span> <span data-ttu-id="eae75-108">소스 제어에 솔루션을 추가 하는 방법에 대 한 자세한 내용은 [소스 제어에 솔루션 추가](../../2014/database-engine/add-solutions-to-source-control.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="eae75-108">For more information about adding solutions to source control, see [Add Solutions to Source Control](../../2014/database-engine/add-solutions-to-source-control.md).</span></span>  
  
 <span data-ttu-id="eae75-109">소스 제어에 솔루션을 추가 하지 않으려는 경우 **소스 제어에 선택 항목 추가** 명령을 사용 하 여 프로젝트를 수동으로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae75-109">If you do not want to add the solution to source control, you can use the **Add Selection to Source Control** command to add the project manually.</span></span>  
  
 <span data-ttu-id="eae75-110">데이터베이스 개체는 원본 제어 공급자가 직접 보호하지 않지만 데이터베이스 개체의 스크립트를 만들어 원본 제어 하에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae75-110">Database objects are not directly protected by the source control provider, but you can create scripts of database objects and save the scripts under source control.</span></span>  
  
### <a name="to-add-a-project-to-source-control"></a><span data-ttu-id="eae75-111">원본 제어에 프로젝트를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="eae75-111">To add a project to source control</span></span>  
  
1.  <span data-ttu-id="eae75-112">솔루션 탐색기에서 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eae75-112">In Solution Explorer, select a project.</span></span>  
  
2.  <span data-ttu-id="eae75-113">**파일** 메뉴에서 **소스 제어**를 가리킨 다음 **원본 제어에 선택한 프로젝트 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="eae75-113">On the **File** menu, point to **Source Control**, and then click **Add Selected Projects to Source Control**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eae75-114">소스 제어 **에 선택한 프로젝트 추가** 명령을 사용 하 여 소스 제어 솔루션에 속한 프로젝트를 추가 하는 경우 프로젝트를 소스 제어 솔루션의 하위 폴더로 추가할지 아니면 프로젝트를 별도의 폴더로 추가할지 묻는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eae75-114">If you use the **Add Selected Projects to Source Control** command to add a project that belongs to a source-controlled solution, you are prompted whether you want to add the project as a subfolder of the source-controlled solution or to add the project as a separate folder.</span></span>  
  
3.  <span data-ttu-id="eae75-115">로그온하라는 메시지가 표시되면 원본 제어 공급자에 로그온합니다.</span><span class="sxs-lookup"><span data-stu-id="eae75-115">If prompted, log on to your source control provider.</span></span>  
  
4.  <span data-ttu-id="eae75-116">**SourceSafe 프로젝트에 추가** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="eae75-116">The **Add to SourceSafe Project** dialog box appears.</span></span> <span data-ttu-id="eae75-117">프로젝트 이름이 **프로젝트** 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="eae75-117">The name of your project appears in the **Project** box.</span></span>  
  
5.  <span data-ttu-id="eae75-118">**폴더** 목록에서 프로젝트를 저장할 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="eae75-118">In the **Folders** list, open the folder where you want to place your project.</span></span> <span data-ttu-id="eae75-119">또는 **만들기** 를 클릭 하 여 **프로젝트** 상자에 이름이 표시 된 폴더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae75-119">Alternatively, you can click **Create** to create a folder with the name displayed in the **Project** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eae75-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eae75-120">See Also</span></span>  
 [<span data-ttu-id="eae75-121">원본 제어에 솔루션 및 프로젝트 추가</span><span class="sxs-lookup"><span data-stu-id="eae75-121">Add Solutions and Projects to Source Control</span></span>](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)  
  
  
