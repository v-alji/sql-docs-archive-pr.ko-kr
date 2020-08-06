---
title: Analysis Services에서 가져오기 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b9a21b23-3a06-4ef8-bc06-9c79cdc54870
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7d6c3d226e46cdb4101bc8db52830046d27b0706
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728827"
---
# <a name="import-from-analysis-services-ssas-tabular"></a><span data-ttu-id="0db9e-102">Analysis Services에서 가져오기(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="0db9e-102">Import from Analysis Services (SSAS Tabular)</span></span>
  <span data-ttu-id="0db9e-103">이 항목에서는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 서버에서 가져오기 프로젝트 템플릿을 사용하여 기존 테이블 형식 모델에서 메타데이터를 가져와서 새로운 테이블 형식 모델 프로젝트를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0db9e-103">This topic describes how to create a new tabular model project by importing the metadata from an existing tabular model by using the Import from Server project template in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="create-a-new-model-by-importing-metadata-from-an-existing-model-in-analysis-services"></a><span data-ttu-id="0db9e-104">Analysis Services의 기존 모델에서 메타데이터를 가져와서 새 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="0db9e-104">Create a new model by importing metadata from an existing model in Analysis Services</span></span>  
 <span data-ttu-id="0db9e-105">서버에서 가져오기 프로젝트 템플릿을 사용하여 Analysis Services 서버의 기존 테이블 형식 모델에서 메타데이터를 복사하여 새로운 테이블 형식 모델 프로젝트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0db9e-105">You can use the Import from Server project template to create a new tabular model project by copying the metadata from an existing tabular model on an Analysis Services server.</span></span> <span data-ttu-id="0db9e-106">메타데이터를 가져온 모델과 동일한 데이터 원본 연결, 테이블, 관계, 측정값, KPI, 역할, 계층, 큐브 뷰 및 파티션을 사용하여 새 프로젝트가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="0db9e-106">The new project will be created with the same data source connections, tables, relationships, measures, KPIs, roles, hierarchies, perspectives, and partitions as the model it was imported from.</span></span> <span data-ttu-id="0db9e-107">하지만 데이터는 기존 모델에서 새 모델 작업 영역으로 복사되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0db9e-107">The data, however, is not copied from the existing model to the new model workspace.</span></span> <span data-ttu-id="0db9e-108">가져오기 프로세스가 완료되고 새 모델 프로젝트가 만들어지면 모두 처리를 실행하여 데이터 원본에서 새 모델 프로젝트 작업 영역 데이터베이스로 데이터를 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db9e-108">Once the import process has completed, and the new model project created, you must run a Process All to load the data from the data sources into the new model project workspace database.</span></span>  
  
#### <a name="to-create-a-new-model-by-importing-metadata-from-an-existing-model"></a><span data-ttu-id="0db9e-109">기존 모델에서 메타데이터를 가져와서 새 모델을 만들려면</span><span class="sxs-lookup"><span data-stu-id="0db9e-109">To create a new model by importing metadata from an existing model</span></span>  
  
1.  <span data-ttu-id="0db9e-110">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]의 **파일** 메뉴에서 **새로 만들기**를 클릭한 다음 **프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0db9e-110">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], on the **File** menu, click **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="0db9e-111">**새 프로젝트** 대화 상자의 **설치된 템플릿**에서 **비즈니스 인텔리전스**를 클릭한 다음 **서버에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0db9e-111">In the **New Project** dialog box, under **Installed Templates**, click **Business Intelligence**, and then click **Import from Server**.</span></span>  
  
3.  <span data-ttu-id="0db9e-112">**이름**에 프로젝트의 이름을 입력하고 위치 및 솔루션 이름을 지정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0db9e-112">In **Name**, type a name for the project, then specify a location and solution name, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="0db9e-113">**Analysis Services에서 가져오기** 대화 상자의 **서버 이름**에서 가져올 모델 메타데이터가 포함된 Analysis Services 서버의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0db9e-113">In the **Import from Analysis Services** dialog box, in **Server Name**, specify the name of the Analysis Services server that contains the model metadata you want to import.</span></span>  
  
5.  <span data-ttu-id="0db9e-114">**데이터베이스 이름**에서 가져올 모델 메타데이터가 포함된 테이블 형식 model 데이터베이스를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0db9e-114">In **Database Name**, select the tabular model database that contains the model metadata you want to import, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0db9e-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0db9e-115">See Also</span></span>  
 [<span data-ttu-id="0db9e-116">프로젝트 속성&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="0db9e-116">Project Properties &#40;SSAS Tabular&#41;</span></span>](properties-ssas-tabular.md)  
  
  
