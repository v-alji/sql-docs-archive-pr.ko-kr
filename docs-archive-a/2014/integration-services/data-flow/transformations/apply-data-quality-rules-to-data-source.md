---
title: 데이터 원본에 데이터 품질 규칙 적용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d59e6fb5ffb752b3346d40740e0b841bf574344e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728516"
---
# <a name="apply-data-quality-rules-to-data-source"></a><span data-ttu-id="b9866-102">데이터 원본에 데이터 품질 규칙 적용</span><span class="sxs-lookup"><span data-stu-id="b9866-102">Apply Data Quality Rules to Data Source</span></span>
  <span data-ttu-id="b9866-103">DQS(Data Quality Services)를 통해 데이터 원본에 DQS 정리 변환을 연결하여 패키지 데이터 흐름의 데이터를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9866-103">You can use Data Quality Services (DQS) to correct data in the package data flow by connecting the DQS Cleansing transformation to the data source.</span></span> <span data-ttu-id="b9866-104">DQS에 대한 자세한 내용은 [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b9866-104">For more information about DQS, see [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md).</span></span> <span data-ttu-id="b9866-105">변환에 대한 자세한 내용은 [DQS Cleansing Transformation](dqs-cleansing-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b9866-105">For more information about the transformation, see [DQS Cleansing Transformation](dqs-cleansing-transformation.md).</span></span>  
  
 <span data-ttu-id="b9866-106">DQS 정리 변환을 사용하여 데이터를 처리할 경우 Data Quality 서버에 데이터 품질 프로젝트가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b9866-106">When you process data with the DQS Cleansing transformation, a data quality project is created on the Data Quality Server.</span></span> <span data-ttu-id="b9866-107">Data Quality 클라이언트를 사용하여 프로젝트를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="b9866-107">You use the Data Quality Client to manage the project.</span></span> <span data-ttu-id="b9866-108">자세한 내용은 [데이터 품질 프로젝트 관리&#40;열기, 잠금 해제, 이름 바꾸기 및 삭제&#41;](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b9866-108">For more information, see [Manage &#40;Open, Unlock, Rename, and Delete&#41; a Data Quality Project](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md).</span></span>  
  
### <a name="to-correct-data-in-the-data-flow"></a><span data-ttu-id="b9866-109">데이터 흐름에서 데이터를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="b9866-109">To correct data in the data flow</span></span>  
  
1.  <span data-ttu-id="b9866-110">패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9866-110">Create a package.</span></span>  
  
2.  <span data-ttu-id="b9866-111">DQS 정리 변환을 구성하고 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b9866-111">Add and configure the DQS Cleansing transformation.</span></span> <span data-ttu-id="b9866-112">자세한 내용은 [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b9866-112">For more information, see [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md).</span></span>  
  
3.  <span data-ttu-id="b9866-113">DQS 정리 변환을 데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b9866-113">Connect the DQS Cleansing transformation to a data source.</span></span>  
  
  
