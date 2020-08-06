---
title: 처리 및 저장소 위치 (파티션 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.specifyprocessingandstorage.f1
ms.assetid: dda2dc57-923d-4db9-93a7-38e95770f3df
author: minewiskan
ms.author: owend
ms.openlocfilehash: 00ab88bac184f57bd2b4dcfdb8d00909a85ece4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741352"
---
# <a name="processing-and-storage-locations-partition-wizard"></a><span data-ttu-id="d4f03-102">처리 및 스토리지 위치(파티션 마법사)</span><span class="sxs-lookup"><span data-stu-id="d4f03-102">Processing and Storage Locations (Partition Wizard)</span></span>
  <span data-ttu-id="d4f03-103">**처리 및 스토리지 위치** 페이지를 사용하여 파티션에 대한 데이터를 저장하는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스뿐만 아니라 해당 파티션을 소유하는 큐브의 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4f03-103">Use the **Processing and Storage Locations** page to specify the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance of the cube that owns the partition, as well as the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that stores the data for the partition.</span></span> <span data-ttu-id="d4f03-104">원격 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스 또는 기본 스토리지 위치 이외의 스토리지 위치를 지정하여 파티션을 원격 파티션으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4f03-104">You can define a partition as a remote partition by specifying either a remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a storage location other than the default storage location.</span></span> <span data-ttu-id="d4f03-105">원격 파티션에 대한 자세한 내용은 [원격 파티션](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4f03-105">For more information about remote partitions, see [Remote Partitions](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md).</span></span>  
  
## <a name="processing-location-options"></a><span data-ttu-id="d4f03-106">처리 위치 옵션</span><span class="sxs-lookup"><span data-stu-id="d4f03-106">Processing location Options</span></span>  
 <span data-ttu-id="d4f03-107">**현재 서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="d4f03-107">**Current server instance**</span></span>  
 <span data-ttu-id="d4f03-108">현재 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에서 파티션을 처리하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4f03-108">Makes the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance responsible for processing the partition.</span></span>  
  
 <span data-ttu-id="d4f03-109">**원격 Analysis Services 데이터 원본**</span><span class="sxs-lookup"><span data-stu-id="d4f03-109">**Remote Analysis Services data source**</span></span>  
 <span data-ttu-id="d4f03-110">원격 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에서 파티션을 처리하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4f03-110">Makes a remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance responsible for processing this partition.</span></span>  
  
 <span data-ttu-id="d4f03-111">드롭다운 목록에서 파티션을 처리할 원격 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스를 나타내는 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4f03-111">From the dropdown list, select the data source representing the remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that will be responsible for processing the partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d4f03-112">`Initial Catalog` 연결 문자열 속성이 유효한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스로 설정되어 있지 않은 데이터 원본을 선택하거나 `Initial Catalog` 연결 문자열 속성에서 지정한 데이터베이스가 원격 파티션을 지원하지 않는 경우, 즉 지정한 데이터베이스의 `MasterDatasourceID` 속성이 유효한 값으로 설정되어 있지 않은 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d4f03-112">An error occurs if you select a data source in which the `Initial Catalog` connection string property is not set to a valid [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, or if the database specified in the `Initial Catalog` connection string property does not support remote partitions (in other words, the `MasterDatasourceID` property of the specified database is not set to a valid value).</span></span>  
  
 <span data-ttu-id="d4f03-113">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="d4f03-113">**New**</span></span>  
 <span data-ttu-id="d4f03-114">파티션을 처리할 원격 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스를 나타내는 새 데이터 원본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d4f03-114">Creates a new data source representing the remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance responsible for processing the partition.</span></span>  
  
## <a name="storage-location-options"></a><span data-ttu-id="d4f03-115">스토리지 위치 옵션</span><span class="sxs-lookup"><span data-stu-id="d4f03-115">Storage location Options</span></span>  
 <span data-ttu-id="d4f03-116">**기본 서버 위치**</span><span class="sxs-lookup"><span data-stu-id="d4f03-116">**Default server location**</span></span>  
 <span data-ttu-id="d4f03-117">현재 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스의 데이터 폴더를 파티션에 대한 집계 및 인덱싱 데이터의 스토리지 위치로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4f03-117">Makes the data folder of the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance the storage location of the aggregation and indexing data for the partition.</span></span>  
  
 <span data-ttu-id="d4f03-118">**지정한 폴더**</span><span class="sxs-lookup"><span data-stu-id="d4f03-118">**Specified folder**</span></span>  
 <span data-ttu-id="d4f03-119">파티션에 대한 집계 및 인덱싱 데이터의 스토리지 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4f03-119">Specifies the storage location of the aggregation and indexing data for the partition.</span></span>  
  
 <span data-ttu-id="d4f03-120">**...**</span><span class="sxs-lookup"><span data-stu-id="d4f03-120">**...**</span></span>  
 <span data-ttu-id="d4f03-121">**지정한 폴더** 에 대한 폴더를 선택할 수 있는 **원격 폴더 찾아보기**대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d4f03-121">Displays the **Browse for Remote Folder** dialog box in which you can select a folder for **Specified folder**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4f03-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4f03-122">See Also</span></span>  
 <span data-ttu-id="d4f03-123">[파티션 마법사 F1 도움말 &#40;Analysis Services 다차원 데이터&#41;](partition-wizard-f1-help-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d4f03-123">[Partition Wizard F1 Help &#40;Analysis Services - Multidimensional Data&#41;](partition-wizard-f1-help-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="d4f03-124">[파티션 &#40;Analysis Services 다차원 데이터&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d4f03-124">[Partitions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="d4f03-125">원격 폴더 찾아보기 대화 상자 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="d4f03-125">Browse for Remote Folder Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)  
  
  
