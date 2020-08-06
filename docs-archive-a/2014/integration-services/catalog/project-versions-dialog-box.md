---
title: 프로젝트 버전 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isprojectprop.versions.f1
ms.assetid: a48a387c-2e70-45bc-be2e-26e57a9bb2c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 998dd194c2a056121fd6f7a404e75c7080b85aa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736681"
---
# <a name="project-versions-dialog-box"></a><span data-ttu-id="860ad-102">프로젝트 버전 대화 상자</span><span class="sxs-lookup"><span data-stu-id="860ad-102">Project Versions Dialog Box</span></span>
  <span data-ttu-id="860ad-103">**프로젝트 버전** 대화 상자를 사용하여 프로젝트 버전을 확인하고 이전 버전으로 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="860ad-103">Use the **Project Versions** dialog box to view versions of a project and to restore a previous version.</span></span>  
  
 <span data-ttu-id="860ad-104">[catalog.object_versions&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-views/catalog-object-versions-ssisdb-database) 뷰에서 이전 버전을 보고 [catalog.restore_project&#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database) 저장 프로시저를 사용하여 이전 버전을 복원할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="860ad-104">You can also view previous versions in the [catalog.object_versions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-versions-ssisdb-database) view, and use the [catalog.restore_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database) stored procedure to restore previous versions.</span></span>  
  
 <span data-ttu-id="860ad-105">**수행 작업**</span><span class="sxs-lookup"><span data-stu-id="860ad-105">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="860ad-106">프로젝트 버전 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="860ad-106">Open the Project Versions dialog box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="860ad-107">프로젝트 버전 복원</span><span class="sxs-lookup"><span data-stu-id="860ad-107">Restore a Project Version</span></span>](#restore)  
  
##  <a name="open-the-project-versions-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="860ad-108">프로젝트 버전 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="860ad-108">Open the Project Versions dialog box</span></span>  
  
1.  <span data-ttu-id="860ad-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="860ad-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="860ad-110">즉, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 데이터베이스를 호스팅하는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="860ad-110">That is, connect to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="860ad-111">개체 탐색기에서 트리를 확장하여 **Integration Services 카탈로그** 노드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="860ad-111">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="860ad-112">**Integration Services 카탈로그** 노드를 확장하여 **SSISDB** 노드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="860ad-112">Expand the **Integration Services Catalogs** node to display the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="860ad-113">**SSISDB** 노드는 각각 하나 이상의 프로젝트를 포함하는 하나 이상의 폴더를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="860ad-113">The **SSISDB** node contains one or more folders that each contain one or more projects.</span></span> <span data-ttu-id="860ad-114">원하는 프로젝트가 포함된 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="860ad-114">Expand the folder that contains the project you are interested in.</span></span>  
  
5.  <span data-ttu-id="860ad-115">프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **버전**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="860ad-115">Right-click the project, and then click **Versions**.</span></span>  
  
 <span data-ttu-id="860ad-116">**프로젝트 버전** 대화 상자에서 **버전** 테이블에는 서버에 배포된 프로젝트의 버전 목록이 표시되고, 해당 버전이 배포된 날짜 및 시간, 버전이 복원된 날짜 및 시간(복원된 경우), 버전 설명 및 버전 식별자가 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="860ad-116">In the **Project Versions** dialog box, the **Versions** table displays the list of versions of the project that have been deployed on the server, with the date and time the version was deployed, the date and time the version was restored (if it was restored), the version description, and a version identifier.</span></span> <span data-ttu-id="860ad-117">현재 활성 버전은 테이블의 **현재** 열에 확인 표시가 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="860ad-117">The currently active version is indicated with a check mark in the **Current** column of the table.</span></span>  
  
##  <a name="restore-a-project-version"></a><a name="restore"></a> <span data-ttu-id="860ad-118">프로젝트 버전 복원</span><span class="sxs-lookup"><span data-stu-id="860ad-118">Restore a Project Version</span></span>  
 <span data-ttu-id="860ad-119">프로젝트의 이전 버전을 복원하려면 **버전** 테이블에서 버전을 선택하고 **선택한 버전으로 복원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="860ad-119">To restore a previous version of a project, select the version in the **Versions** table, and then click **Restore to Selected Version**.</span></span> <span data-ttu-id="860ad-120">프로젝트가 선택한 버전으로 복원되고 해당 버전은 **버전** 테이블의 **현재** 열에 확인 표시가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="860ad-120">The project is restored to the selected version and that version is indicated with a check mark in the **Current** column of the **Versions** table.</span></span>  
  
  
