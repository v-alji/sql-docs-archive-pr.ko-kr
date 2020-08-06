---
title: 속성 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a59d3448-8619-4044-923b-8effba926dfa
author: minewiskan
ms.author: owend
ms.openlocfilehash: f1d8c77ffbe8e185e15b716819498fe48295348e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728748"
---
# <a name="properties-ssas-tabular"></a><span data-ttu-id="08b76-102">속성(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="08b76-102">Properties (SSAS Tabular)</span></span>
  <span data-ttu-id="08b76-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 의 테이블 형식 모델 프로젝트에는 프로젝트, 모델, 보고 및 배포를 위한 동작을 정의하는 다양한 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08b76-103">Tabular model projects in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] have various properties that define behaviors for the project, model, reporting, and deployment.</span></span> <span data-ttu-id="08b76-104">속성 설정은 Model.bim 파일에 XML 형식으로 저장되지만, 이 섹션에서 설명하는 모든 속성은 **의** 속성 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]창에서 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08b76-104">Property settings are stored in XML format in the Model.bim file, however, all of the properties described in this section can be configured in the **Properties** windows in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="08b76-105">관련 작업</span><span class="sxs-lookup"><span data-stu-id="08b76-105">Related Tasks</span></span>  
  
|<span data-ttu-id="08b76-106">항목</span><span class="sxs-lookup"><span data-stu-id="08b76-106">Topic</span></span>|<span data-ttu-id="08b76-107">Description</span><span class="sxs-lookup"><span data-stu-id="08b76-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="08b76-108">파워 뷰 보고 속성&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="08b76-108">Power View Reporting Properties &#40;SSAS Tabular&#41;</span></span>](power-view-reporting-properties-ssas-tabular.md)|<span data-ttu-id="08b76-109">이 섹션의 항목에서는 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]에 연결되고 여기서 검색되는 테이블 형식 모델에 대한 설명과 구성 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="08b76-109">Topics in this section provide descriptions and configuration options for tabular models that will be connected to and browsed from [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>|  
|[<span data-ttu-id="08b76-110">프로젝트 속성&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="08b76-110">Project Properties &#40;SSAS Tabular&#41;</span></span>](project-properties-ssas-tabular.md)|<span data-ttu-id="08b76-111">프로젝트 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="08b76-111">Provides descriptions for project properties.</span></span> <span data-ttu-id="08b76-112">프로젝트 속성에는 프로젝트 파일 및 배포 옵션 설정이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="08b76-112">Project properties include project file and deployment options settings.</span></span>|  
|[<span data-ttu-id="08b76-113">모델 속성&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="08b76-113">Model Properties &#40;SSAS Tabular&#41;</span></span>](model-properties-ssas-tabular.md)|<span data-ttu-id="08b76-114">모델 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="08b76-114">Provides descriptions for model properties.</span></span> <span data-ttu-id="08b76-115">모델 속성은 모델을 제작하는 동안 모델 프로젝트의 빌드 동작, 백업 및 작업 영역 데이터베이스에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="08b76-115">Model properties affect the model project's build actions, backup, and workspace database during model authoring.</span></span>|  
|[<span data-ttu-id="08b76-116">테이블 속성&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="08b76-116">Table Properties &#40;SSAS Tabular&#41;</span></span>](table-properties-ssas-tabular.md)|<span data-ttu-id="08b76-117">기본 테이블 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="08b76-117">Provides descriptions for basic table properties.</span></span> <span data-ttu-id="08b76-118">여기에서 설명하는 테이블 속성은 원본에 있는 열을 표시하고 선택 및 필터링할 수 있도록 하는 테이블 속성 편집 대화 상자의 테이블 속성과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="08b76-118">Table properties described here are different from those in the Edit Table Properties dialog box, which display and allow selection and filtering of columns from the source,</span></span>|  
|[<span data-ttu-id="08b76-119">열 속성&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="08b76-119">Column Properties &#40;SSAS Tabular&#41;</span></span>](column-properties-ssas-tabular.md)|<span data-ttu-id="08b76-120">열 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="08b76-120">Provides descriptions for column properties.</span></span> <span data-ttu-id="08b76-121">열 속성은 열의 데이터 형식, 형식 및 숨기기 설정을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="08b76-121">Column properties define a column's data type, format, and hiding settings.</span></span>|  
|[<span data-ttu-id="08b76-122">기본 데이터 모델링 및 배포 속성 구성&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="08b76-122">Configure Default Data Modeling and Deployment Properties &#40;SSAS Tabular&#41;</span></span>](configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)|<span data-ttu-id="08b76-123">기본 모델링 및 배포 속성에 대한 설명 및 구성 단계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="08b76-123">Provides descriptions and configuration steps for default modeling and deployment properties.</span></span> <span data-ttu-id="08b76-124">기본 속성은 새 테이블 형식 모델 프로젝트에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="08b76-124">Default properties apply to new tabular model projects.</span></span> <span data-ttu-id="08b76-125">프로젝트를 만든 후 요구 사항에 따라 특정 모델 프로젝트에 대해 이러한 속성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08b76-125">After a project is created, these properties can be changed for a particular model project depending on your requirements.</span></span>|  
  
  
