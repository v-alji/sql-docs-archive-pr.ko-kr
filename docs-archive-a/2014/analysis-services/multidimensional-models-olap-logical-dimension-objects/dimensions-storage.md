---
title: 차원 저장소 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], storage
- storing data [Analysis Services]
- storage [Analysis Services], dimensions
- relational OLAP
- multidimensional OLAP
- MOLAP
- storing data [Analysis Services], dimensions
- ROLAP
ms.assetid: 8d74b932-2174-4e1f-8414-636455880b6a
author: minewiskan
ms.author: owend
ms.openlocfilehash: afa68ebcfa8f4136bcd4a131842c852665ee9851
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728912"
---
# <a name="dimension-storage"></a><span data-ttu-id="93a1c-102">차원 스토리지</span><span class="sxs-lookup"><span data-stu-id="93a1c-102">Dimension Storage</span></span>
  <span data-ttu-id="93a1c-103">의 차원은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 다음 두 가지 저장소 모드를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="93a1c-103">Dimensions in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] support two storage modes:</span></span>  
  
-   <span data-ttu-id="93a1c-104">ROLAP(관계형 OLAP)</span><span class="sxs-lookup"><span data-stu-id="93a1c-104">Relational OLAP (ROLAP)</span></span>  
  
-   <span data-ttu-id="93a1c-105">MOLAP(다차원 OLAP)</span><span class="sxs-lookup"><span data-stu-id="93a1c-105">Multidimensional OLAP (MOLAP)</span></span>  
  
 <span data-ttu-id="93a1c-106">스토리지 모드에 따라 차원 데이터의 위치와 형식이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="93a1c-106">The storage mode determines the location and form of a dimension's data.</span></span> <span data-ttu-id="93a1c-107">MOLAP은 차원의 기본 스토리지 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="93a1c-107">MOLAP is the default storage mode for dimensions.</span></span> <span data-ttu-id="93a1c-108">**관련 항목:**[파티션 저장소 모드 및 처리](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)</span><span class="sxs-lookup"><span data-stu-id="93a1c-108">**Related topics:**[Partition Storage Modes and Processing](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)</span></span>  
  
## <a name="molap"></a><span data-ttu-id="93a1c-109">MOLAP</span><span class="sxs-lookup"><span data-stu-id="93a1c-109">MOLAP</span></span>  
 <span data-ttu-id="93a1c-110">MOLAP을 사용하는 차원의 데이터는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 다차원 구조에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="93a1c-110">Data for a dimension that uses MOLAP is stored in a multidimensional structure in the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="93a1c-111">이 다차원 구조는 차원이 처리될 때 생성되고 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="93a1c-111">This multidimensional structure is created and populated when the dimension is processed.</span></span> <span data-ttu-id="93a1c-112">MOLAP 차원은 ROLAP 차원보다 우수한 쿼리 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="93a1c-112">MOLAP dimensions provide better query performance than ROLAP dimensions.</span></span>  
  
## <a name="rolap"></a><span data-ttu-id="93a1c-113">ROLAP</span><span class="sxs-lookup"><span data-stu-id="93a1c-113">ROLAP</span></span>  
 <span data-ttu-id="93a1c-114">ROLAP을 사용하는 차원의 데이터는 실제로 차원 정의에 사용되는 테이블에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="93a1c-114">Data for a dimension that uses ROLAP is actually stored in the tables used to define the dimension.</span></span> <span data-ttu-id="93a1c-115">ROLAP 스토리지 모드를 사용하면 대량의 데이터를 복제하지 않고도 대규모 차원을 지원할 수 있는 대신 쿼리 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="93a1c-115">The ROLAP storage mode can be used to support large dimensions without duplicating large amounts of data, but at the expense of query performance.</span></span> <span data-ttu-id="93a1c-116">차원은 해당 차원을 정의하는 데 사용한 데이터 원본 뷰의 테이블을 직접 사용하기 때문에 ROLAP 스토리지 모드에서 실시간 OLAP도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="93a1c-116">Because the dimension relies directly on the tables in the data source view used to define the dimension, the ROLAP storage mode also supports real-time OLAP.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="93a1c-117">차원이 ROLAP 스토리지 모드를 사용하며 MOLAP 스토리지를 사용하는 큐브에 차원이 포함되어 있는 경우 해당 원본 테이블에 대한 스키마가 변경될 때마다 큐브를 바로 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93a1c-117">If a dimension uses the ROLAP storage mode and the dimension is included in a cube that uses MOLAP storage, any schema changes to its source table must be followed by immediate processing of the cube.</span></span> <span data-ttu-id="93a1c-118">그렇지 않으면 큐브를 쿼리할 때 결과에 일관성이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93a1c-118">Failure to do this may result in inconsistent results when querying the cube.</span></span> <span data-ttu-id="93a1c-119">**관련 항목:**[SSIS를 사용 하 여 관리 작업 Analysis Services 자동화](../instances/automate-analysis-services-administrative-tasks-with-ssis.md)</span><span class="sxs-lookup"><span data-stu-id="93a1c-119">**Related topic:**[Automate Analysis Services Administrative Tasks with SSIS](../instances/automate-analysis-services-administrative-tasks-with-ssis.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a1c-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="93a1c-120">See Also</span></span>  
 [<span data-ttu-id="93a1c-121">파티션 스토리지 모드 및 처리</span><span class="sxs-lookup"><span data-stu-id="93a1c-121">Partition Storage Modes and Processing</span></span>](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
  
