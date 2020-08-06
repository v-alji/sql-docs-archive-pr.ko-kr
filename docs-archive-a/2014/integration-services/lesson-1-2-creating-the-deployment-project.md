---
title: '2단계: 배포 프로젝트 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 59990fe2-7036-4e9c-8efc-6ece9e66eda7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ebfce8796f98628c2832c5ab7f4be665c7915d10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651137"
---
# <a name="step-2-creating-the-deployment-project"></a><span data-ttu-id="bf16f-102">2단계: 배포 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="bf16f-102">Step 2: Creating the Deployment Project</span></span>
  <span data-ttu-id="bf16f-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]에서 배포 가능한 단위는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="bf16f-103">In [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the deployable unit is an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="bf16f-104">패키지를 배포할 수 있으려면 새 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 만들고 모든 패키지 및 패키지와 함께 배포할 모든 보조 파일을 해당 프로젝트에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf16f-104">Before you can deploy packages, you must create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project and add all the packages and any ancillary files that you want to deploy with the packages to that project.</span></span>  
  
### <a name="to-create-the-integration-services-project"></a><span data-ttu-id="bf16f-105">Integration Services 프로젝트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="bf16f-105">To create the Integration Services project</span></span>  
  
1.  <span data-ttu-id="bf16f-106">**시작**을 클릭하고 **모든 프로그램**, **Microsoft SQL Server**를 차례로 가리킨 후 **SQL Server Data Tools**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf16f-106">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL ServerSQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="bf16f-107">**파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트** 를 클릭하여 새 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bf16f-107">On the **File** menu, point to **New**, and then click **Project** to create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
3.  <span data-ttu-id="bf16f-108">**새 프로젝트** 대화 상자의 **템플릿** 창에서 **Integration Services 프로젝트** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bf16f-108">In the **New Project** dialog box, select **Integration Services Project** in the **Templates** pane.</span></span>  
  
4.  <span data-ttu-id="bf16f-109">**이름** 상자에서 기본 이름을 **Deployment Tutorial**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="bf16f-109">In the **Name** box, change the default name to **Deployment Tutorial**.</span></span> <span data-ttu-id="bf16f-110">필요에 따라 **솔루션용 디렉터리 만들기** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="bf16f-110">Optionally, clear the **Create directory for solution** check box.</span></span>  
  
5.  <span data-ttu-id="bf16f-111">기본 위치를 적용하거나 **찾아보기** 를 클릭하여 사용할 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="bf16f-111">Accept the default location, or click **Browse** to locate the folder you want to use.</span></span>  
  
6.  <span data-ttu-id="bf16f-112">**프로젝트 위치** 대화 상자에서 해당 폴더를 클릭한 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf16f-112">In the **Project Location** dialog box, click the folder, and then click **Open**.</span></span>  
  
7.  <span data-ttu-id="bf16f-113">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf16f-113">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="bf16f-114">기본적으로 Package.dtsx라는 빈 패키지가 만들어지고 프로젝트에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf16f-114">By default, an empty package, named Package.dtsx, is created and added to your project.</span></span> <span data-ttu-id="bf16f-115">그러나 이 패키지를 사용하는 대신에 기존 패키지를 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bf16f-115">However, you will not use this package; instead, you will add existing packages to the project.</span></span> <span data-ttu-id="bf16f-116">프로젝트의 모든 패키지가 배포에 포함되므로 Package.dtsx를 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf16f-116">Because all the packages in a project will be included in the deployment, you should delete Package.dtsx.</span></span> <span data-ttu-id="bf16f-117">이 패키지를 삭제하려면 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf16f-117">To delete it, right-click it, and then click **Delete**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="bf16f-118">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="bf16f-118">Next Task in Lesson</span></span>  
 [<span data-ttu-id="bf16f-119">3단계: 패키지 및 기타 파일 추가</span><span class="sxs-lookup"><span data-stu-id="bf16f-119">Step 3: Adding Packages and Other Files</span></span>](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
<span data-ttu-id="bf16f-120">![Integration Services 아이콘 (작은 아이콘)](media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="bf16f-120">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="bf16f-121">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="bf16f-121">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="bf16f-122">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="bf16f-122">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="bf16f-123">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="bf16f-123">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf16f-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bf16f-124">See Also</span></span>  
 [<span data-ttu-id="bf16f-125">Integration Services&#40;SSIS&#41; 프로젝트</span><span class="sxs-lookup"><span data-stu-id="bf16f-125">Integration Services &#40;SSIS&#41; Projects</span></span>](integration-services-ssis-projects-and-solutions.md)  
  
  
