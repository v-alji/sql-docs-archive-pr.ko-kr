---
title: '1단계: 새 Integration Services 프로젝트 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f14521b5-941e-443b-8f5e-385f98e37fbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d6d16d7febcdecb01eb7a93167c2a18d225a9c2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651143"
---
# <a name="step-1-creating-a-new-integration-services-project"></a><span data-ttu-id="7bfc5-102">1단계: 새 Integration Services 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="7bfc5-102">Step 1: Creating a New Integration Services Project</span></span>
  <span data-ttu-id="7bfc5-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 패키지를 만드는 첫 번째 단계는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-103">The first step in creating a package in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] is to create an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="7bfc5-104">이 프로젝트는 데이터 변환 솔루션에서 사용하는 데이터 원본, 데이터 원본 뷰, 패키지 등의 개체에 대한 템플릿을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-104">This project includes the templates for the objects - data sources, data source views, and packages - that you use in a data transformation solution.</span></span>  
  
 <span data-ttu-id="7bfc5-105">이 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 자습서에서 만들 패키지는 로캘 구분 데이터의 값을 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-105">The packages that you will create in this [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] tutorial interpret the values of locale-sensitive data.</span></span> <span data-ttu-id="7bfc5-106">컴퓨터가 영어(미국) 국가별 옵션을 사용하도록 구성되어 있지 않은 경우 패키지에 추가 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-106">If your computer is not configured to use the regional option English (United States), you need to set additional properties in the package.</span></span> <span data-ttu-id="7bfc5-107">2-5단원에서 사용하는 패키지는 1단원에서 만든 패키지에서 복사한 것이므로 복사된 패키지의 로캘 구분 속성을 업데이트할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-107">The packages that you use in lessons 2 through 5 are copied from the package created in lesson 1, and you need not update locale-sensitive properties in the copied packages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bfc5-108">이 자습서를 사용하려면 Microsoft SQL Server Data Tools가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-108">This tutorial requires Microsoft SQL Server Data Tools.</span></span>  
>   
>  <span data-ttu-id="7bfc5-109">SQL Server Data Tools 설치 방법에 대한 자세한 내용은 [SQL Server Data Tools 다운로드](https://msdn.microsoft.com/data/hh297027)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-109">For more information on installing the SQL Server Data Tools see [SQL Server Data Tools Download](https://msdn.microsoft.com/data/hh297027).</span></span>  
  
### <a name="to-create-a-new-integration-services-project"></a><span data-ttu-id="7bfc5-110">새 Integration Services 프로젝트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="7bfc5-110">To create a new Integration Services project</span></span>  
  
1.  <span data-ttu-id="7bfc5-111">**시작** 메뉴에서 **모든 프로그램**, **Microsoft SQL Server**를 차례로 가리킨 다음 **SQL Server Data Tools**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-111">On the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server**, and click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="7bfc5-112">**파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트** 를 클릭하여 새 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-112">On the **File** menu, point to **New**, and click **Project** to create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
3.  <span data-ttu-id="7bfc5-113">**새 프로젝트** 대화 상자의 **설치된 템플릿** 아래에서 **비즈니스 인텔리전스**를 확장하고 **템플릿** 창에서 **통합 서비스 프로젝트** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-113">In the **New Project** dialog box, expand the **Business Intelligence** node under **Installed Templates**, and select **Integration Services Project** in the **Templates** pane.</span></span>  
  
4.  <span data-ttu-id="7bfc5-114">**이름** 상자에서 기본 이름을 **SSIS Tutorial**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-114">In the **Name** box, change the default name to **SSIS Tutorial**.</span></span> <span data-ttu-id="7bfc5-115">필요에 따라 **솔루션용 디렉터리 만들기** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-115">Optionally, clear the **Create directory for solution** check box.</span></span>  
  
5.  <span data-ttu-id="7bfc5-116">기본 위치를 적용하거나 **찾아보기** 를 클릭하여 사용할 폴더를 찾아 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-116">Accept the default location, or click **Browse** to browse to locate the folder you want to use.</span></span> <span data-ttu-id="7bfc5-117">**프로젝트 위치** 대화 상자에서 해당 폴더를 클릭한 다음 **폴더 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-117">In the **Project Location** dialog box, click the folder and click **Select Folder**.</span></span>  
  
6.  <span data-ttu-id="7bfc5-118">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-118">Click **OK**.</span></span>  
  
     <span data-ttu-id="7bfc5-119">기본적으로 **Package.dtsx**라는 빈 패키지가 만들어지고 SSIS 패키지 아래 프로젝트에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-119">By default, an empty package, titled **Package.dtsx**, will be created and added to your project under SSIS Packages.</span></span>  
  
7.  <span data-ttu-id="7bfc5-120">**솔루션 탐색기** 도구 모음에서 **Package.dtsx**를 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 클릭한 다음 기본 패키지의 이름을 **Lesson 1.dtsx**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7bfc5-120">In **Solution Explorer** toolbar, right-click **Package.dtsx**, click **Rename**, and rename the default package to **Lesson 1.dtsx**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="7bfc5-121">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="7bfc5-121">Next Task in Lesson</span></span>  
 [<span data-ttu-id="7bfc5-122">2단계: 플랫 파일 연결 관리자 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="7bfc5-122">Step 2: Adding and Configuring a Flat File Connection Manager</span></span>](lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
  
