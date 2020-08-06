---
title: 새 모델 페이지 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 27d5bf66-b0e7-489e-a830-ffe2ec8e5350
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ed591108585b494ebb4498c1a0ab3e782693a45b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653234"
---
# <a name="new-model-page-report-manager"></a><span data-ttu-id="bd69f-102">새 모델 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="bd69f-102">New Model Page (Report Manager)</span></span>
  <span data-ttu-id="bd69f-103">이 페이지를 사용하여 공유 데이터 원본에서 기본 보고서 모델을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-103">Use this page to generate a default report model from a shared data source.</span></span> <span data-ttu-id="bd69f-104">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 다차원 데이터 원본, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 관계형 데이터 원본, 그리고 Oracle 관계형 데이터 원본에서만 보고서 모델을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-104">You can only generate report models from [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional data sources, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] relational data sources, and Oracle relational data sources.</span></span>  
  
 <span data-ttu-id="bd69f-105">보고서 관리자에서 생성하는 모델은 공유 데이터 원본의 스키마를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-105">Models that you generate in Report Manager are based on the schema of the shared data source.</span></span> <span data-ttu-id="bd69f-106">엔터티, 폴더 및 필드는 데이터 원본의 모든 테이블 및 열에 대해 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-106">Entities, folders, and fields are created for all tables and columns in the data source.</span></span> <span data-ttu-id="bd69f-107">항목을 제외할 수 없으며, 모델이 생성되는 방법을 결정하는 옵션도 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-107">You cannot exclude items, nor can you set options that determine how the model is generated.</span></span> <span data-ttu-id="bd69f-108">모델을 사용자 지정하거나 구체화하려면 모델 디자이너를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-108">If you want to customize or refine a model, you must use Model Designer instead.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="bd69f-109">탐색</span><span class="sxs-lookup"><span data-stu-id="bd69f-109">Navigation</span></span>  
 <span data-ttu-id="bd69f-110">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="bd69f-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-model-page"></a><span data-ttu-id="bd69f-111">새 모델 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="bd69f-111">To open the New Model page</span></span>  
  
1.  <span data-ttu-id="bd69f-112">보고서 관리자를 열고 모델을 생성하려는 공유 데이터 원본을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-112">Open Report Manager, and locate the shared data source from which you want to generate a model.</span></span>  
  
2.  <span data-ttu-id="bd69f-113">데이터 원본 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-113">Hover over the data source, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="bd69f-114">드롭다운 메뉴에서 다음 단계 중 하나를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="bd69f-114">In the drop-down menu, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="bd69f-115">**보고서 모델 생성** 을 클릭하여 새 모델 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-115">Click **Generate Report Model** to open the New Model page.</span></span>  
  
    -   <span data-ttu-id="bd69f-116">**관리** 를 클릭하여 보고서의 일반 속성 페이지를 연 다음</span><span class="sxs-lookup"><span data-stu-id="bd69f-116">Click **Manage** to open the General properties page for the report.</span></span> <span data-ttu-id="bd69f-117">**모델 생성** 을 클릭하여 새 모델 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-117">Then click **Generate Model** to open the New Model page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bd69f-118">옵션</span><span class="sxs-lookup"><span data-stu-id="bd69f-118">Options</span></span>  
 <span data-ttu-id="bd69f-119">**이름**</span><span class="sxs-lookup"><span data-stu-id="bd69f-119">**Name**</span></span>  
 <span data-ttu-id="bd69f-120">모델의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-120">Specifies the name of the model.</span></span> <span data-ttu-id="bd69f-121">이름은 하나 이상의 영숫자 문자를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-121">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="bd69f-122">공백과 특정 기호도 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-122">It can also include spaces and some symbols.</span></span> <span data-ttu-id="bd69f-123">이름 지정 시에는 다음 문자를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="bd69f-123">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="bd69f-124">; ?</span><span class="sxs-lookup"><span data-stu-id="bd69f-124">; ?</span></span> <span data-ttu-id="bd69f-125">: \@ & = +, $/\* \< > | " /</span><span class="sxs-lookup"><span data-stu-id="bd69f-125">: \@ & = + , $ / \* \< > | " /</span></span>  
  
 <span data-ttu-id="bd69f-126">**설명**</span><span class="sxs-lookup"><span data-stu-id="bd69f-126">**Description**</span></span>  
 <span data-ttu-id="bd69f-127">모델에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-127">Shows a description of the model.</span></span> <span data-ttu-id="bd69f-128">보고서 관리자를 통해 이 항목을 보는 사용자는 폴더 계층을 검색할 때 이 설명을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-128">Users who view this item through Report Manager see this description when browsing the folder hierarchy.</span></span>  
  
 <span data-ttu-id="bd69f-129">**위치 변경**</span><span class="sxs-lookup"><span data-stu-id="bd69f-129">**Change Location**</span></span>  
 <span data-ttu-id="bd69f-130">새 모델의 폴더 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-130">Shows the folder location for the new model.</span></span> <span data-ttu-id="bd69f-131">**위치 변경** 단추를 클릭하여 다른 위치를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd69f-131">You can click the **Change Location** button to select a different location.</span></span>  
  
  
