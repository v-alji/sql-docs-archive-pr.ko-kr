---
title: 매개 변수 값 설정 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ce9c2201-4e9a-4495-948f-b68deeaa7955
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 637267603c66921a566ca0d2a3f49f6142cfd203
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736669"
---
# <a name="set-parameter-value-dialog-box"></a><span data-ttu-id="0cd4b-102">매개 변수 값 설정 대화 상자</span><span class="sxs-lookup"><span data-stu-id="0cd4b-102">Set Parameter Value Dialog Box</span></span>
  <span data-ttu-id="0cd4b-103">**매개 변수 값 설정** 대화 상자를 사용하여 패키지 및 프로젝트에 대한 매개 변수 및 연결 관리자 속성 값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cd4b-103">Use the **Set Parameter Value** dialog box to set values for parameters and connection manager properties, for projects and packages.</span></span>  
  
 <span data-ttu-id="0cd4b-104">**수행 작업**</span><span class="sxs-lookup"><span data-stu-id="0cd4b-104">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="0cd4b-105">매개 변수 값 설정 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="0cd4b-105">Open the Set Parameter Value dialog box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="0cd4b-106">옵션 구성</span><span class="sxs-lookup"><span data-stu-id="0cd4b-106">Configure the options</span></span>](#option)  
  
##  <a name="open-the-set-parameter-value-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="0cd4b-107">매개 변수 값 설정 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="0cd4b-107">Open the Set Parameter Value dialog box</span></span>  
  
1.  <span data-ttu-id="0cd4b-108">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd4b-108">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="0cd4b-109">SSISDB 데이터베이스를 호스팅하는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd4b-109">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="0cd4b-110">개체 탐색기에서 트리를 확장하여 **Integration Services 카탈로그** 노드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd4b-110">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="0cd4b-111">**SSISDB** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd4b-111">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="0cd4b-112">패키지 또는 프로젝트를 마우스 오른쪽 단추로 클릭하고 **구성**을 클릭한 다음 **매개 변수** 탭 또는 **연결 관리자** 탭에서 줄임표 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd4b-112">Right-click a package or project, click **Configure**, and then click the ellipsis button in the **Parameters** tab or in the **Connection Managers** tab.</span></span>  
  
##  <a name="configure-the-options"></a><a name="option"></a> <span data-ttu-id="0cd4b-113">옵션 구성</span><span class="sxs-lookup"><span data-stu-id="0cd4b-113">Configure the options</span></span>  
 <span data-ttu-id="0cd4b-114">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="0cd4b-114">**Parameter**</span></span>  
 <span data-ttu-id="0cd4b-115">매개 변수 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd4b-115">Lists the parameter name.</span></span>  
  
 <span data-ttu-id="0cd4b-116">**형식**</span><span class="sxs-lookup"><span data-stu-id="0cd4b-116">**Type**</span></span>  
 <span data-ttu-id="0cd4b-117">매개 변수 값의 데이터 형식을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd4b-117">Lists the data type of the parameter value.</span></span>  
  
 <span data-ttu-id="0cd4b-118">**설명**</span><span class="sxs-lookup"><span data-stu-id="0cd4b-118">**Description**</span></span>  
 <span data-ttu-id="0cd4b-119">매개 변수에 대한 선택적 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd4b-119">Shows an optional description for the parameter.</span></span>  
  
 <span data-ttu-id="0cd4b-120">**값 편집**</span><span class="sxs-lookup"><span data-stu-id="0cd4b-120">**Edit value**</span></span>  
 <span data-ttu-id="0cd4b-121">매개 변수 값을 편집하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd4b-121">Select this option to edit the parameter value.</span></span>  
  
 <span data-ttu-id="0cd4b-122">**패키지에서 기본값 사용**</span><span class="sxs-lookup"><span data-stu-id="0cd4b-122">**Use default value from package**</span></span>  
 <span data-ttu-id="0cd4b-123">패키지에 저장된 기본 매개 변수 값을 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd4b-123">Select this option to use the default parameter value stored in the package.</span></span>  
  
 <span data-ttu-id="0cd4b-124">**환경 변수 사용**</span><span class="sxs-lookup"><span data-stu-id="0cd4b-124">**Use environment variable**</span></span>  
 <span data-ttu-id="0cd4b-125">프로젝트 또는 패키지에서 참조하는 환경에 저장된 변수 값을 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd4b-125">Select this option to use a variable value stored in the environment, which is referenced by the project or package.</span></span> <span data-ttu-id="0cd4b-126">프로젝트 또는 패키지에 대한 환경 참조를 추가하려면 **구성** 대화 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd4b-126">To add an environment reference to a project or package, use the **Configure** dialog box.</span></span> <span data-ttu-id="0cd4b-127">자세한 내용은 [Configure Dialog Box](configure-dialog-box.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0cd4b-127">For more information, see [Configure Dialog Box](configure-dialog-box.md).</span></span>  
  
  
