---
title: 패키지 속성 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackageprop.general.f1
- sql12.ssis.ssms.packageproperties.f1
ms.assetid: a70acbf4-5f5c-4606-8ce4-8eb3684233de
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b386bf4e75ff784cd8d4a96363515786d242d2a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649638"
---
# <a name="package-properties-dialog-box"></a><span data-ttu-id="98de6-102">패키지 속성 대화 상자</span><span class="sxs-lookup"><span data-stu-id="98de6-102">Package Properties Dialog Box</span></span>
  <span data-ttu-id="98de6-103">**패키지 속성** 대화 상자를 사용하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 저장된 패키지의 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98de6-103">Use the **Package Properties** dialog box to view properties for packages that are stored on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="98de6-104">자세한 내용은 [Integration Services&#40;SSIS&#41; 패키지](integration-services-ssis-server-and-catalog.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98de6-104">For more information, see [Integration Services &#40;SSIS&#41; Server](integration-services-ssis-server-and-catalog.md).</span></span>  
  
 <span data-ttu-id="98de6-105">**수행 작업**</span><span class="sxs-lookup"><span data-stu-id="98de6-105">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="98de6-106">패키지 속성 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="98de6-106">Open the Package Properties dialog box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="98de6-107">옵션 구성</span><span class="sxs-lookup"><span data-stu-id="98de6-107">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-package-properties-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="98de6-108">패키지 속성 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="98de6-108">Open the Package Properties dialog box</span></span>  
  
1.  <span data-ttu-id="98de6-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="98de6-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="98de6-110">SSISDB 데이터베이스를 호스팅하는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="98de6-110">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="98de6-111">개체 탐색기에서 트리를 확장하여 **Integration Services 카탈로그** 노드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98de6-111">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="98de6-112">**SSISDB** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="98de6-112">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="98de6-113">속성을 확인할 패키지가 포함된 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="98de6-113">Expand the folder that contains the package you want to view properties for.</span></span>  
  
5.  <span data-ttu-id="98de6-114">패키지를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="98de6-114">Right-click the package, and then select **Properties**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="98de6-115">옵션 구성</span><span class="sxs-lookup"><span data-stu-id="98de6-115">Configure the Options</span></span>  
 <span data-ttu-id="98de6-116">**일반** 페이지를 사용하여 선택한 패키지의 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98de6-116">Use the **General** page to view the properties of the selected package.</span></span>  
  
 <span data-ttu-id="98de6-117">**일반** 페이지에 표시된 속성은 모두 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="98de6-117">All properties on the **General** page are read-only.</span></span>  
  
 <span data-ttu-id="98de6-118">**이름**</span><span class="sxs-lookup"><span data-stu-id="98de6-118">**Name**</span></span>  
 <span data-ttu-id="98de6-119">패키지의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98de6-119">Displays the name of the package.</span></span>  
  
 <span data-ttu-id="98de6-120">**식별자**</span><span class="sxs-lookup"><span data-stu-id="98de6-120">**Identifier**</span></span>  
 <span data-ttu-id="98de6-121">패키지 ID를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="98de6-121">Lists the package ID.</span></span>  
  
 <span data-ttu-id="98de6-122">**진입점**</span><span class="sxs-lookup"><span data-stu-id="98de6-122">**Entry Point**</span></span>  
 <span data-ttu-id="98de6-123">`True` 값은 패키지가 직접 시작됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="98de6-123">The value of `True` indicates that the package is started directly.</span></span> <span data-ttu-id="98de6-124">`False` 값은 패키지가 패키지 실행 태스크로 다른 패키지에 의해 시작됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="98de6-124">The value of `False` indicates that the package is started by another package using the Execute Package task.</span></span> <span data-ttu-id="98de6-125">기본값은 `True`입니다.</span><span class="sxs-lookup"><span data-stu-id="98de6-125">The default value is `True`.</span></span>  
  
 <span data-ttu-id="98de6-126">솔루션 탐색기에서 패키지를 마우스 오른쪽 단추로 클릭하고 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 진입점 패키지 **를 클릭하여**에서 부모 패키지 및 자식 패키지 모두에 대해 이 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="98de6-126">You set this property in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] for both the parent package and the child packages by right-clicking the package in Solution Explorer and then clicking **Entry-point Package**.</span></span>  
  
 <span data-ttu-id="98de6-127">**설명**</span><span class="sxs-lookup"><span data-stu-id="98de6-127">**Description**</span></span>  
 <span data-ttu-id="98de6-128">패키지에 대한 설명(옵션)을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98de6-128">Displays the optional description of the package.</span></span>  
  
  
