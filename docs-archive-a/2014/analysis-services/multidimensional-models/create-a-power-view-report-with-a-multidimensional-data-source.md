---
title: 다차원 데이터 원본을 사용 하 여 파워 뷰 보고서 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b9b6f4c9-7e1f-4f61-b657-8986e39a6af2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 179bb9eed94cd0dbb579bdb06d630b213339d12f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737053"
---
# <a name="create-a-power-view-report-with-a-multidimensional-data-source"></a><span data-ttu-id="fca60-102">다차원 데이터 원본이 포함된 파워 뷰 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="fca60-102">Create a Power View Report with a Multidimensional Data Source</span></span>
  <span data-ttu-id="fca60-103">다차원 모델을 기반으로 Power View 보고서를 만드는 것은 PowerPivot 통합 문서나 Analysis Services 테이블 형식 모델을 기반으로 보고서를 만드는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fca60-103">Creating a Power View report based on a multidimensional model is no different than creating a report based on a PowerPivot workbook or an Analysis Services Tabular model.</span></span> <span data-ttu-id="fca60-104">파워 뷰 보고서는 SharePoint 라이브러리의 보고서 데이터 원본 연결 파일(.rsds)에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="fca60-104">Power View reports are created from a Report Data Source connection file (.rsds) in a SharePoint library.</span></span> <span data-ttu-id="fca60-105">.rsds를 만드는 방법에 대한 자세한 내용은 [Create a Report Data Source](create-a-report-data-source.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fca60-105">For more information about how to create an .rsds, see [Create a Report Data Source](create-a-report-data-source.md).</span></span>  
  
 <span data-ttu-id="fca60-106">시작하기 전에 다음을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fca60-106">Before you begin, you need to know:</span></span>  
  
-   <span data-ttu-id="fca60-107">다차원 모델에 대한 공유 보고서 데이터 원본 연결(.rsds)이 포함된 SharePoint 라이브러리의 이름과 위치.</span><span class="sxs-lookup"><span data-stu-id="fca60-107">The name and location of the SharePoint library that contains a shared report data source connection (.rsds) to a multidimensional model.</span></span>  
  
#### <a name="create-a-new-blank-power-view-report"></a><span data-ttu-id="fca60-108">비어 있는 새 파워 뷰 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="fca60-108">Create a new, blank Power View report</span></span>  
  
-   <span data-ttu-id="fca60-109">SharePoint 라이브러리에서 .rsds 공유 보고서 데이터 원본 연결(다차원 모델에 연결되는 .rsds) 옆의 화살표를 클릭한 다음 **파워 뷰 보고서 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fca60-109">In the SharePoint library, click the arrow next to the .rsds shared report data source connection (the .rsds that connects to the multidimensional model), and then click **Create Power View Report**.</span></span>  
  
  
