---
title: 파티션 마법사 F1 도움말 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Partition Wizard
ms.assetid: 3b6d7053-aeef-4d9e-af70-f5b40256e859
author: minewiskan
ms.author: owend
ms.openlocfilehash: fa8c0e94c2b18ffbd1228752bd7cb4ad4f684acb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648641"
---
# <a name="partition-wizard-f1-help-analysis-services---multidimensional-data"></a><span data-ttu-id="62a64-102">파티션 마법사 F1 도움말(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="62a64-102">Partition Wizard F1 Help (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="62a64-103">파티션 마법사를 사용하여 측정값 그룹에 대한 파티션을 큐브에 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62a64-103">You can use the Partition Wizard to define partitions for a measure group in a cube.</span></span> <span data-ttu-id="62a64-104">기본적으로 큐브의 각 측정값 그룹에 대해 단일 파티션이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="62a64-104">By default, a single partition is defined for each measure group in a cube.</span></span> <span data-ttu-id="62a64-105">그러나 파티션이 크면 액세스 및 처리 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62a64-105">Access and processing performance, however, can degrade for large partitions.</span></span> <span data-ttu-id="62a64-106">각각 측정값 그룹의 일부 데이터를 포함하는 여러 파티션을 만들면 측정값 그룹의 액세스 및 처리 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62a64-106">By creating multiple partitions, each containing a portion of the data for a measure group, you can improve the access and processing performance for that measure group.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="62a64-107">**원본 정보 지정** 또는 **행 제한** 페이지에 중복 행을 포함하면 잘못된 데이터가 포함된 파티션이 생성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62a64-107">It is possible to create partitions that may contain incorrect data by including duplicate rows in the **Specify Source Information** or **Restrict Rows** pages.</span></span>  
  
 <span data-ttu-id="62a64-108">파티션 마법사는 다음 단계로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62a64-108">The Partition Wizard guides you through the following steps:</span></span>  
  
-   <span data-ttu-id="62a64-109">파티션에 대한 데이터 원본 뷰 선택</span><span class="sxs-lookup"><span data-stu-id="62a64-109">Selecting the data source view for the partition.</span></span>  
  
-   <span data-ttu-id="62a64-110">파티션에 포함된 레코드에 대한 필터 생성</span><span class="sxs-lookup"><span data-stu-id="62a64-110">Creating a filter for the records included in the partition.</span></span>  
  
-   <span data-ttu-id="62a64-111">처리 및 스토리지 위치 설정</span><span class="sxs-lookup"><span data-stu-id="62a64-111">Setting the processing and storage locations.</span></span>  
  
-   <span data-ttu-id="62a64-112">파티션 이름 지정 및 저장</span><span class="sxs-lookup"><span data-stu-id="62a64-112">Naming and saving the partition.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="62a64-113">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="62a64-113">In This Section</span></span>  
  
-   [<span data-ttu-id="62a64-114">파티션 &#40;원본 정보 지정 마법사&#41;</span><span class="sxs-lookup"><span data-stu-id="62a64-114">Specify Source Information &#40;Partition Wizard&#41;</span></span>](specify-source-information-partition-wizard.md)  
  
-   [<span data-ttu-id="62a64-115">파티션 &#40;행 제한 마법사&#41;</span><span class="sxs-lookup"><span data-stu-id="62a64-115">Restrict Rows &#40;Partition Wizard&#41;</span></span>](restrict-rows-partition-wizard.md)  
  
-   [<span data-ttu-id="62a64-116">처리 및 저장소 위치 &#40;파티션 마법사&#41;</span><span class="sxs-lookup"><span data-stu-id="62a64-116">Processing and Storage Locations &#40;Partition Wizard&#41;</span></span>](processing-and-storage-locations-partition-wizard.md)  
  
-   [<span data-ttu-id="62a64-117">마법사 &#40;파티션 마법사를 완료 하는 중&#41;</span><span class="sxs-lookup"><span data-stu-id="62a64-117">Completing the Wizard &#40;Partition Wizard&#41;</span></span>](completing-the-wizard-partition-wizard.md)  
  
-   [<span data-ttu-id="62a64-118">원격 폴더 찾아보기 대화 상자 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="62a64-118">Browse for Remote Folder Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)  
  
## <a name="see-also"></a><span data-ttu-id="62a64-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="62a64-119">See Also</span></span>  
 [<span data-ttu-id="62a64-120">파티션&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="62a64-120">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
