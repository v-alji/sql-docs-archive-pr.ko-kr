---
title: 프로젝트 가져오기 마법사 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.importprojectwizard.f1
ms.assetid: 9247ad6c-4bd1-43ab-b347-583181cb9917
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 81a990995d7e98c21b61f484372d31c9a1773102
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651190"
---
# <a name="import-project-wizard"></a><span data-ttu-id="27392-102">프로젝트 가져오기 마법사</span><span class="sxs-lookup"><span data-stu-id="27392-102">Import Project Wizard</span></span>
  <span data-ttu-id="27392-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트 가져오기 마법사를 사용하여 기존 항목에 따라 새 Integration Services 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27392-103">Use the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Import Project Wizard create a new Integration Services project based on an existing one.</span></span> <span data-ttu-id="27392-104">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 카탈로그에 이미 배포된 프로젝트를 가져오거나 프로젝트 배포 파일(확장명 .ispac)에서 프로젝트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="27392-104">Import projects that have already been deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog or import projects from a project deployment file (.ispac extension).</span></span>  
  
### <a name="to-create-a-project-based-on-a-project-in-ispac-file-or-in-catalog"></a><span data-ttu-id="27392-105">.ispac 파일 또는 카탈로그의 프로젝트를 기반으로 프로젝트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="27392-105">To create a project based on a project in .ispac file or in catalog</span></span>  
  
1.  <span data-ttu-id="27392-106">**파일**을 클릭 하 고 **새로 만들기**를 가리킨 다음 프로젝트를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="27392-106">Click **File**, point to **New**, and click Project.</span></span>  
  
2.  <span data-ttu-id="27392-107">**비즈니스 인텔리전스**를 확장하고 **Integration Services**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27392-107">Expand **Business Intelligence**, and click **Integration Services**.</span></span>  
  
3.  <span data-ttu-id="27392-108">가운데 창에서 **Integration Services 가져오기 마법사** 를 선택하고 솔루션, 프로젝트에 대한 **이름** 을 입력하고 프로젝트에 대한 **폴더** 를 지정한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27392-108">Select **Integration Services Import Wizard** in the middle pane, type a **name** for the solution, project, and specify the **folder** for the project, and then click **OK**.</span></span>  
  
     <span data-ttu-id="27392-109">**Integration Services 프로젝트 가져오기 마법사**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="27392-109">You should see the **Integration Services Import Project Wizard**.</span></span> <span data-ttu-id="27392-110">이 마법사는 기존 항목에 따라 새 Integration Services 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27392-110">This wizard creates a new Integration Services project based on an existing one</span></span>  
  
4.  <span data-ttu-id="27392-111">**소개** 페이지에서 **다음** 을 클릭하여 **원본 선택** 페이지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="27392-111">Click **Next** on the **Introduction** page to see the **Select Source** page.</span></span>  
  
5.  <span data-ttu-id="27392-112">.ispac 파일 또는 카탈로그에서 프로젝트를 가져올지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27392-112">Specify whether you want to import project from an .ispac file or from a catalog.</span></span>  
  
    -   <span data-ttu-id="27392-113">**프로젝트 배포 파일** 옵션을 선택한 경우 .ispac 파일에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27392-113">If you select **Project deployment file** option, specify the path to the .ispac file.</span></span>  
  
    -   <span data-ttu-id="27392-114">**Integration Services 카탈로그** 옵션을 선택한 경우 카탈로그가 있는 데이터베이스 서버 인스턴스의 이름을 지정하고 카탈로그에서 프로젝트에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27392-114">If you select **Integration Services Catalog** option, specify the name of database server instance on which the catalog exists, and the path to the project in the catalog.</span></span>  
  
6.  <span data-ttu-id="27392-115">**원본 선택** 페이지에서 **다음** 을 클릭하여 **검토** 페이지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="27392-115">Click **Next** on the **Select Source** page to see the **Review** page.</span></span> <span data-ttu-id="27392-116">페이지에 표시된 마법사가 수행하려는 가져오기 작업에 대한 정보를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="27392-116">Review the information displayed on the page about the import operation the wizard is going to perform.</span></span>  
  
7.  <span data-ttu-id="27392-117">**가져오기** 를 클릭하여 사용자가 선택한 항목에 따라 새 Integration Services 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27392-117">Click **Import** to create a new Integration Services project based on the one you selected.</span></span>  
  
8.  <span data-ttu-id="27392-118">**결과** 페이지에 마법사가 수행한 가져오기 작업의 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="27392-118">The **Results** page should display the results from import operation the wizard performed.</span></span> <span data-ttu-id="27392-119">**보고서 저장** 을 클릭하여 보고서를 XML 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="27392-119">Click **Save Report** to save the report to an XML file.</span></span>  
  
9. <span data-ttu-id="27392-120">**닫기**를 클릭하여 마법사를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="27392-120">Click **Close** to close the wizard.</span></span>  
  
  
