---
title: 파티션 병합 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- merging partitions [XMLA]
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
ms.assetid: 657e1d4d-6d50-40f8-a771-7b20c9d865f8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 65840066d3e95571db511a2015a1bee64aa8d922
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649759"
---
# <a name="merging-partitions-xmla"></a><span data-ttu-id="98bf5-102">파티션 병합(XMLA)</span><span class="sxs-lookup"><span data-stu-id="98bf5-102">Merging Partitions (XMLA)</span></span>
  <span data-ttu-id="98bf5-103">파티션의 집계 디자인 및 구조가 동일한 경우 XML for Analysis (XMLA)에서 [Mergepartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) 명령을 사용 하 여 파티션을 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98bf5-103">If partitions have the same aggregation design and structure, you can merge the partition by using the [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) command in XML for Analysis (XMLA).</span></span> <span data-ttu-id="98bf5-104">파티션 병합은 파티션을 관리할 때 수행하는 중요한 동작으로, 특히 날짜별로 파티션된 기록 데이터가 들어 있는 파티션을 관리하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="98bf5-104">Merging partitions is an important action to perform when you manage partitions, especially those partitions that contain historical data partitioned by date.</span></span>  
  
 <span data-ttu-id="98bf5-105">예를 들어, 재무 큐브에서 다음과 같은 파티션 2개를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98bf5-105">For example, a financial cube may use two partitions:</span></span>  
  
-   <span data-ttu-id="98bf5-106">한 파티션은 올해의 재무 데이터를 나타내며 성능을 위해 실시간 ROLAP(관계형 OLAP) 스토리지 설정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98bf5-106">One partition represents financial data for the current year, using real-time relational OLAP (ROLAP) storage settings for performance.</span></span>  
  
-   <span data-ttu-id="98bf5-107">다른 파티션은 작년의 재무 데이터를 나타내며 저장을 위해 MOLAP(다차원 OLAP) 스토리지 설정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98bf5-107">Another partition contains financial data for previous years, using multidimensional OLAP (MOLAP) storage settings for storage.</span></span>  
  
 <span data-ttu-id="98bf5-108">두 파티션에 사용된 스토리지 설정은 서로 다르지만 집계 디자인은 같습니다.</span><span class="sxs-lookup"><span data-stu-id="98bf5-108">Both partitions use different storage settings, but use the same aggregation design.</span></span> <span data-ttu-id="98bf5-109">연말에 기록 데이터를 연도별로 처리하는 방식으로 큐브를 처리하는 대신 `MergePartitions` 명령을 사용하여 올해의 파티션을 작년의 파티션에 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98bf5-109">Instead of processing the cube across years of historical data at the end of the year, you can instead use the `MergePartitions` command to merge the partition for the current year into the partition for previous years.</span></span> <span data-ttu-id="98bf5-110">이렇게 하면 많은 시간이 소요될 수 있는 전체 큐브 처리 작업을 수행하지 않고도 집계 데이터를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98bf5-110">This preserves the aggregation data without requiring a potentially time-consuming full processing of the cube.</span></span>  
  
## <a name="specifying-partitions-to-merge"></a><span data-ttu-id="98bf5-111">병합할 파티션 지정</span><span class="sxs-lookup"><span data-stu-id="98bf5-111">Specifying Partitions to Merge</span></span>  
 <span data-ttu-id="98bf5-112">`MergePartitions`명령이 실행 되 면 [source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) 속성에 지정 된 원본 파티션에 저장 된 집계 데이터가 [대상](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) 속성에 지정 된 대상 파티션에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98bf5-112">When the `MergePartitions` command runs, the aggregation data stored in the source partitions specified in the [Source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) property is added to the target partition specified in the [Target](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98bf5-113">`Source` 속성은 둘 이상의 파티션 개체 참조를 가질 수 있지만</span><span class="sxs-lookup"><span data-stu-id="98bf5-113">The `Source` property can contain more than one partition object reference.</span></span> <span data-ttu-id="98bf5-114">`Target` 속성은 그럴 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98bf5-114">However, the `Target` property cannot.</span></span>  
  
 <span data-ttu-id="98bf5-115">`Source` 및 `Target`에 모두 지정된 파티션을 성공적으로 병합하려면 두 속성이 같은 측정값 그룹에 포함되어야 하고 같은 집계 디자인을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98bf5-115">To be successfully merged, the partitions specified in both the `Source` and `Target` must be contained by the same measure group and use the same aggregation design.</span></span> <span data-ttu-id="98bf5-116">그렇지 않으면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="98bf5-116">Otherwise, an error occurs.</span></span>  
  
 <span data-ttu-id="98bf5-117">`Source`에 지정된 파티션은 `MergePartitions` 명령이 완료된 후 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="98bf5-117">The partitions specified in the `Source` are deleted after the `MergePartitions` command is successfully completed.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="98bf5-118">예</span><span class="sxs-lookup"><span data-stu-id="98bf5-118">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="98bf5-119">Description</span><span class="sxs-lookup"><span data-stu-id="98bf5-119">Description</span></span>  
 <span data-ttu-id="98bf5-120">다음 예에서는 **놀이 works DW** 예제 데이터베이스에 있는 **어드벤처 works** 큐브의 **Customer 개수** 측정값 그룹에 있는 모든 파티션을 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **Customers_2004** 파티션에 병합 합니다.</span><span class="sxs-lookup"><span data-stu-id="98bf5-120">The following example merges all the partitions in the **Customer Counts** measure group of the **Adventure Works** cube in the **Adventure Works DW** sample [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database into the **Customers_2004** partition.</span></span>  
  
### <a name="code"></a><span data-ttu-id="98bf5-121">코드</span><span class="sxs-lookup"><span data-stu-id="98bf5-121">Code</span></span>  
  
```  
<MergePartitions xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2001</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2002</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2003</PartitionID>  
    </Source>  
  </Sources>  
  <Target>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2004</PartitionID>  
  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a><span data-ttu-id="98bf5-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98bf5-122">See Also</span></span>  
 [<span data-ttu-id="98bf5-123">Analysis Services에서 XMLA를 사용하여 개발</span><span class="sxs-lookup"><span data-stu-id="98bf5-123">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
