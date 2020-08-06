---
title: 데이터 원본 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6908998b-9302-4a90-976e-770106b48d18
author: minewiskan
ms.author: owend
ms.openlocfilehash: d686d8100e30d7608e8d90f135022bdf46785723
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733280"
---
# <a name="data-sources-ssas-tabular"></a><span data-ttu-id="88e80-102">데이터 원본(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="88e80-102">Data Sources (SSAS Tabular)</span></span>
  <span data-ttu-id="88e80-103">데이터 원본은 테이블 형식 모델 솔루션에 포함될 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="88e80-103">Data sources provide the data to be included in a tabular model solution.</span></span> <span data-ttu-id="88e80-104">관계형 데이터베이스, 데이터 피드, 다차원 데이터 원본(Analysis Services 큐브 등) 및 텍스트 파일(Microsoft Excel 통합 문서 등) 등의 다양한 원본에서 모델로 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88e80-104">You can import data into your model from a wide variety of sources such as relational databases, data feeds, multidimensional data sources such as an Analysis Services cube, and from text files such as a Microsoft Excel workbook.</span></span> <span data-ttu-id="88e80-105">이 섹션의 항목에서는 데이터를 가져올 수 있는 데이터 원본의 유형, 가져올 수 있는 다양한 데이터 형식 및 이러한 원본에서 데이터를 가져오는 방법을 설명하는 태스크에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="88e80-105">Topics in this section provide information about the types of data sources you can import from, the various data types you can import, and tasks describing how to import data from those sources.</span></span>  
  
## <a name="related-topics-and-tasks"></a><span data-ttu-id="88e80-106">관련 항목 및 태스크</span><span class="sxs-lookup"><span data-stu-id="88e80-106">Related Topics and Tasks</span></span>  
  
|<span data-ttu-id="88e80-107">항목</span><span class="sxs-lookup"><span data-stu-id="88e80-107">Topic</span></span>|<span data-ttu-id="88e80-108">설명</span><span class="sxs-lookup"><span data-stu-id="88e80-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="88e80-109">지원되는 데이터 원본&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="88e80-109">Data Sources Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-sources-supported-ssas-tabular.md)|<span data-ttu-id="88e80-110">이 항목에서는 데이터를 가져올 수 있는 다양한 데이터 원본에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="88e80-110">This topic provides information about the different data sources that you can import data from.</span></span>|  
|[<span data-ttu-id="88e80-111">지원되는 데이터 형식&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="88e80-111">Data Types Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-types-supported-ssas-tabular.md)|<span data-ttu-id="88e80-112">이 항목에서는 테이블 형식 모델에서 지원되는 다양한 데이터 형식에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="88e80-112">This topic provides information about the various data types that are supported in a Tabular Model.</span></span>|  
|[<span data-ttu-id="88e80-113">가장&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="88e80-113">Impersonation &#40;SSAS Tabular&#41;</span></span>](tabular-models/impersonation-ssas-tabular.md)|<span data-ttu-id="88e80-114">이 항목에서는 데이터 원본에 연결하여 데이터를 가져오고 새로 고칠 때 사용되는 로그온 자격 증명을 제공하는 가장에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="88e80-114">This topic provides information about impersonation, which provides logon credentials that are used by Analysis Services when connecting to a data source to import and refresh data.</span></span>|  
|[<span data-ttu-id="88e80-115">데이터 가져오기&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="88e80-115">Import Data &#40;SSAS Tabular&#41;</span></span>](import-data-ssas-tabular.md)|<span data-ttu-id="88e80-116">이 섹션의 태스크는 서로 다른 데이터 원본에서 데이터를 가져오는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="88e80-116">Tasks in this section describe how to import data from different data sources.</span></span>|  
|[<span data-ttu-id="88e80-117">데이터 처리&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="88e80-117">Process Data &#40;SSAS Tabular&#41;</span></span>](process-data-ssas-tabular.md)|<span data-ttu-id="88e80-118">이 섹션의 태스크는 모델로 이미 가져온 데이터를 처리(새로 고침)하거나 변경하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="88e80-118">Tasks in this section describe how to process (refresh) or change data that has already been imported into a model.</span></span>|  
|[<span data-ttu-id="88e80-119">기존 데이터 원본 연결 편집&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="88e80-119">Edit an Existing Data Source Connection &#40;SSAS Tabular&#41;</span></span>](edit-an-existing-data-source-connection-ssas-tabular.md)|<span data-ttu-id="88e80-120">이미 만들어서 원본에서 데이터를 가져오는 데 사용된 데이터 원본 연결을 편집하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="88e80-120">Describes how to edit a data source connection that has already been created and used to import data from a source.</span></span>|  
  
  
