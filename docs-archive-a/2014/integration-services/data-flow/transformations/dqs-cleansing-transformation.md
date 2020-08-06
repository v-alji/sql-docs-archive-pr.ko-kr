---
title: DQS 정리 변환 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data correction
- correct data
ms.assetid: d2ec1b1a-c745-4741-b57c-6fdb524a154c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e980497905b8fa96a73516916af17f934221992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646562"
---
# <a name="dqs-cleansing-transformation"></a><span data-ttu-id="4b718-102">DQS 정리 변환</span><span class="sxs-lookup"><span data-stu-id="4b718-102">DQS Cleansing Transformation</span></span>
  <span data-ttu-id="4b718-103">DQS 정리 변환은 DQS(Data Quality Services)를 통해, 데이터 원본 또는 유사한 데이터 원본에 대해 만든 승인된 규칙을 적용하여 연결된 데이터 원본에서 데이터를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b718-103">The DQS Cleansing transformation uses Data Quality Services (DQS) to correct data from a connected data source, by applying approved rules that were created for the connected data source or a similar data source.</span></span> <span data-ttu-id="4b718-104">데이터 수정 규칙에 대한 자세한 내용은 [DQS Knowledge Bases and Domains](../../../data-quality-services/dqs-knowledge-bases-and-domains.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4b718-104">For more information about data correction rules, see [DQS Knowledge Bases and Domains](../../../data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span> <span data-ttu-id="4b718-105">DQS에 대한 자세한 내용은 [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4b718-105">For more information DQS, see [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md).</span></span>  
  
 <span data-ttu-id="4b718-106">데이터를 수정해야 할지 여부를 확인하기 위해 DQS 정리 변환은 다음과 같은 조건이 충족되는 경우 입력 열의 데이터를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="4b718-106">To determine whether the data has to be corrected, the DQS Cleansing transformation processes data from an input column when the following conditions are true:</span></span>  
  
-   <span data-ttu-id="4b718-107">데이터 수정을 위해 열이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b718-107">The column is selected for data correction.</span></span>  
  
-   <span data-ttu-id="4b718-108">열 데이터 형식에 데이터 수정이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b718-108">The column data type is supported for data correction.</span></span>  
  
-   <span data-ttu-id="4b718-109">열은 호환 가능한 데이터 형식의 도메인에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b718-109">The column is mapped a domain that has a compatible data type.</span></span>  
  
 <span data-ttu-id="4b718-110">변환에는 행 수준 오류를 처리하기 위해 구성할 수 있는 오류 출력이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b718-110">The transformation also includes an error output that you configure to handle row-level errors.</span></span> <span data-ttu-id="4b718-111">오류 출력을 구성하려면 **DQS 정리 변환 편집기**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4b718-111">To configure the error output, use the **DQS Cleansing Transformation Editor**.</span></span>  
  
 <span data-ttu-id="4b718-112">데이터 흐름에 [Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) 을 포함하여 중복된 것으로 간주되는 데이터 행을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b718-112">You can include the [Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) in the data flow to identify rows of data that are likely to be duplicates.</span></span>  
  
## <a name="data-quality-projects-and-values"></a><span data-ttu-id="4b718-113">데이터 품질 프로젝트 및 값</span><span class="sxs-lookup"><span data-stu-id="4b718-113">Data Quality Projects and Values</span></span>  
 <span data-ttu-id="4b718-114">DQS 정리 변환으로 데이터를 처리하면 Data Quality 서버에 정리 프로젝트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b718-114">When you process data with the DQS Cleansing transformation, a cleansing project is created on the Data Quality Server.</span></span> <span data-ttu-id="4b718-115">Data Quality 클라이언트를 사용하여 프로젝트를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="4b718-115">You use the Data Quality Client to manage the project.</span></span> <span data-ttu-id="4b718-116">또한 Data Quality 클라이언트를 사용하여 프로젝트 값을 DQS 기술 자료 도메인으로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b718-116">In addition, you can use the Data Quality Client to import the project values into a DQS knowledge base domain.</span></span> <span data-ttu-id="4b718-117">값만 도메인(또는 연결된 도메인)으로 가져올 수 있으며, DQS 정리 변환은 해당 도메인을 사용하도록 구성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4b718-117">You can import the values only to a domain (or linked domain) that the DQS Cleansing transformation was configured to use.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="4b718-118">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4b718-118">Related Tasks</span></span>  
  
-   [<span data-ttu-id="4b718-119">Data Quality Client에서 Integration Services 프로젝트 열기</span><span class="sxs-lookup"><span data-stu-id="4b718-119">Open Integration Services Projects in Data Quality Client</span></span>](../../../data-quality-services/open-integration-services-projects-in-data-quality-client.md)  
  
-   [<span data-ttu-id="4b718-120">도메인으로 정리 프로젝트 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="4b718-120">Import Cleansing Project Values into a Domain</span></span>](../../../data-quality-services/import-cleansing-project-values-into-a-domain.md)  
  
-   [<span data-ttu-id="4b718-121">데이터 원본에 데이터 품질 규칙 적용</span><span class="sxs-lookup"><span data-stu-id="4b718-121">Apply Data Quality Rules to Data Source</span></span>](apply-data-quality-rules-to-data-source.md)  
  
## <a name="related-content"></a><span data-ttu-id="4b718-122">관련 내용</span><span class="sxs-lookup"><span data-stu-id="4b718-122">Related Content</span></span>  
  
-   [<span data-ttu-id="4b718-123">데이터 품질 프로젝트&#41; 열기, 잠금 해제, 이름 바꾸기 및 삭제 &#40;관리</span><span class="sxs-lookup"><span data-stu-id="4b718-123">Manage &#40;Open, Unlock, Rename, and Delete&#41; a Data Quality Project</span></span>](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)  
  
-   <span data-ttu-id="4b718-124">social.technet.microsoft.com의 문서, [복합 도메인을 사용하여 복합 데이터 정리](https://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx)</span><span class="sxs-lookup"><span data-stu-id="4b718-124">Article, [Cleansing complex data using composite domains](https://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx), on social.technet.microsoft.com.</span></span>  
  
  
