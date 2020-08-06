---
title: 새 Integration Services 프로젝트 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Integration Services], creating
- Integration Services projects, creating
- SQL Server Integration Services projects, creating
- SSIS projects, creating
ms.assetid: 1e23f259-0401-4333-ab4f-89809aae63b1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f62d3ac2d33bb51a0ccc3b77d9f8b5ec0f52b345
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649617"
---
# <a name="create-a-new-integration-services-project"></a><span data-ttu-id="ec069-102">새 Integration Services 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="ec069-102">Create a New Integration Services Project</span></span>
  <span data-ttu-id="ec069-103">이 절차에서는 새 프로젝트와 새 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 솔루션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ec069-103">This procedure creates a new project and a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] solution.</span></span>  
  
### <a name="to-create-a-new-integration-services-project"></a><span data-ttu-id="ec069-104">새 Integration Services 프로젝트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="ec069-104">To create a new Integration Services project</span></span>  
  
1.  <span data-ttu-id="ec069-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ec069-105">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="ec069-106">**파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ec069-106">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="ec069-107">**새 프로젝트** 대화 상자의 **템플릿** 창에서 **Integration Services 프로젝트** 템플릿을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ec069-107">In the **New Project** dialog box, in the **Templates** pane, select the **Integration Services Project** template.</span></span>  
  
     <span data-ttu-id="ec069-108">**Integration Services 프로젝트** 템플릿은 비어 있는 단일 패키지가 포함되어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ec069-108">The **Integration Services Project** template creates an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains a single, empty package.</span></span>  
  
4.  <span data-ttu-id="ec069-109">(선택 사항) 프로젝트 이름과 위치를 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="ec069-109">(Optional) Edit the project name and the location.</span></span>  
  
     <span data-ttu-id="ec069-110">솔루션 이름은 프로젝트 이름과 일치하도록 자동으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec069-110">The solution name is automatically updated to match the project name.</span></span>  
  
5.  <span data-ttu-id="ec069-111">솔루션 파일에 대한 별개의 폴더를 만들려면 **솔루션용 디렉터리 만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ec069-111">To create a separate folder for the solution file, select **Create directory for solution**.</span></span> <span data-ttu-id="ec069-112">기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="ec069-112">This is the default option.</span></span>  
  
6.  <span data-ttu-id="ec069-113">컴퓨터에 원본 제어 소프트웨어가 설치된 경우 **원본 제어에 추가**  를 선택하여 프로젝트와 원본 제어를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ec069-113">If source control software is installed on the computer, select **Add to source control**  to associate the project with source control.</span></span>  
  
7.  <span data-ttu-id="ec069-114">원본 제어 소프트웨어가 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe인 경우 **Visual SourceSafe 로그인** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ec069-114">If the source control software is [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, the **Visual SourceSafe Login** dialog box opens.</span></span> <span data-ttu-id="ec069-115">**Visual SourceSafe 로그인**에서 사용자 이름, 암호 및 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe 데이터베이스의 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ec069-115">In **Visual SourceSafe Login**, provide a user name, a password, and the name of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe database.</span></span> <span data-ttu-id="ec069-116">데이터베이스를 찾으려면 **찾아보기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ec069-116">Click **Browse** to locate the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ec069-117">선택한 원본 제어 플러그 인을 확인 및 변경하고 원본 제어 환경을 구성하려면 **도구** 메뉴에서 **옵션**을 클릭한 후 **원본 제어** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ec069-117">To view and change the selected source control plug-in and to configure the source control environment, click **Options** on the **Tools** menu, and then expand the **Source Control** node.</span></span>  
  
8.  <span data-ttu-id="ec069-118">**확인** 을 클릭 하 여 솔루션을 **솔루션에**추가 하 고 솔루션에 프로젝트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec069-118">Click **OK** to add the solution to **Solution Explore**r and add the project to the solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec069-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ec069-119">See Also</span></span>  
 <span data-ttu-id="ec069-120">[SSIS&#41; 프로젝트 &#40;Integration Services](integration-services-ssis-projects-and-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="ec069-120">[Integration Services &#40;SSIS&#41; Projects](integration-services-ssis-projects-and-solutions.md) </span></span>  
 [<span data-ttu-id="ec069-121">솔루션에서 Integration Services 프로젝트 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="ec069-121">Add or Remove an Integration Services Project in a Solution</span></span>](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)  
  
  
