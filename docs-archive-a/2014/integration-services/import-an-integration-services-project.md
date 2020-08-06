---
title: Integration Services 프로젝트 가져오기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3301c328-b0f5-4517-915c-93713413e453
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a98219f3a04d11e086957d64a62e7c64cd51418
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647128"
---
# <a name="import-an-integration-services-project"></a><span data-ttu-id="dca19-102">Integration Services 프로젝트 가져오기</span><span class="sxs-lookup"><span data-stu-id="dca19-102">Import an Integration Services Project</span></span>
  <span data-ttu-id="dca19-103">기존 배포 파일(.ispac) 또는 Integration Services 카탈로그에 배포된 프로젝트에서 프로젝트를 만들려면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]**프로젝트 가져오기 마법사**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-103">Use the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]**Import Project Wizard** to create a project from an existing deployment file (.ispac) or from a project deployed to Integration services catalog.</span></span> <span data-ttu-id="dca19-104">이 기능은 프로젝트의 원본이 없지만 .ispac 파일 또는 SSISDB 카탈로그에서 프로젝트를 만들려는 경우에 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-104">This feature is especially useful when you do not have the original copy of the project but you want to create one from an .ispac file or SSISDB catalog.</span></span>  
  
### <a name="to-import-a-project"></a><span data-ttu-id="dca19-105">프로젝트를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="dca19-105">To Import a Project</span></span>  
  
1.  <span data-ttu-id="dca19-106">의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **New**  >  **파일** 메뉴에서 새**프로젝트** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-106">In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], click **New** > **Project** on the **File** menu.</span></span>  
  
2.  <span data-ttu-id="dca19-107">**새 프로젝트** 창의 **설치되어 있는 템플릿** 영역에서 **비즈니스 인텔리전스**를 확장하고 **Integration Services**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-107">In the **Installed Templates** area of the **New Project** window, expand **Business Intelligence**, and click **Integration Services**.</span></span>  
  
3.  <span data-ttu-id="dca19-108">프로젝트 형식 목록에서 **Integration Services 프로젝트 가져오기 마법사** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-108">Select **Integration Services Import Project Wizard** from the project types list.</span></span>  
  
4.  <span data-ttu-id="dca19-109">**이름** 입력란에 만들 새 프로젝트의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-109">Type a name for the new project to be created in the **Name** text box.</span></span>  
  
5.  <span data-ttu-id="dca19-110">**위치** 입력란에 프로젝트의 경로 또는 위치를 입력하거나 **찾아보기** 를 클릭하여 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-110">Type the path or location for the project in the **Location** text box, or click **Browse** to select one.</span></span>  
  
6.  <span data-ttu-id="dca19-111">**솔루션 이름** 입력란에 솔루션의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-111">Type a name for the solution in the **Solution name** text box.</span></span>  
  
7.  <span data-ttu-id="dca19-112">**확인** 을 클릭하여 **Integration Services 프로젝트 가져오기 마법사** 대화 상자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-112">Click **OK** to launch the **Integration Services Import Project Wizard** dialog box.</span></span>  
  
8.  <span data-ttu-id="dca19-113">**다음** 을 클릭하여 **원본 선택** 페이지로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-113">Click **Next** to switch to the **Select Source** page.</span></span>  
  
9. <span data-ttu-id="dca19-114">**.ispac** 파일에서 가져오는 경우 **경로** 입력란에 파일 이름을 포함한 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-114">If you are importing from an **.ispac** file, type the path including file name in the **Path** text box.</span></span> <span data-ttu-id="dca19-115">**찾아보기** 를 클릭하여 솔루션을 저장할 폴더로 이동하고 **파일 이름** 입력란에 파일 이름을 입력한 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-115">Click **Browse** to navigate to the folder where you want the solution to be stored and type file name in the **File name** text box, and click **Open**.</span></span>  
  
     <span data-ttu-id="dca19-116">**Integration Services 카탈로그**에서 가져오는 경우 **서버 이름** 입력란에 데이터베이스 인스턴스 이름을 입력하거나 **찾아보기** 를 클릭하고 카탈로그가 들어 있는 데이터베이스 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-116">If you are importing from an **Integration Services Catalog**, type the database instance name in the **Server name** text box or click **Browse** and select the database instance that contains the catalog.</span></span>  
  
     <span data-ttu-id="dca19-117">**경로** 입력란 옆의 **찾아보기** 를 클릭하고 카탈로그에서 폴더를 확장한 다음 가져올 프로젝트를 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-117">Click **Browse** next to **Path** text box, expand folder in the catalog, select the project you want to import, and click **OK**.</span></span>  
  
     <span data-ttu-id="dca19-118">**다음** 을 클릭하여 **검토** 페이지로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-118">Click **Next** to switch to the **Review** page.</span></span>  
  
10. <span data-ttu-id="dca19-119">정보를 검토하고 **가져오기** 를 클릭하여 선택한 기존 프로젝트를 기반으로 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-119">Review the information and click **Import** to create a project based on the existing project you selected.</span></span>  
  
11. <span data-ttu-id="dca19-120">선택 사항: **보고서 저장** 을 클릭하여 결과를 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-120">Optional: click **Save Report** to save the results to a file</span></span>  
  
12. <span data-ttu-id="dca19-121">**닫기** 를 클릭하여 **Integration Services 프로젝트 가져오기 마법사** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="dca19-121">Click **Close** to close the **Integration Services Import Project Wizard** dialog box.</span></span>  
  
  
