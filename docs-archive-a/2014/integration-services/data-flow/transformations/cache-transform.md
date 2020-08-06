---
title: 캐시 변환 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.cachetrans.f1
helpviewer_keywords:
- Cache transform
ms.assetid: a5683fc8-9c32-4634-819e-e9815627e4f1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 34be3252a3caf344c95e13ae45cc485a8c4ffdc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652243"
---
# <a name="cache-transform"></a><span data-ttu-id="e78f1-102">캐시 변환</span><span class="sxs-lookup"><span data-stu-id="e78f1-102">Cache Transform</span></span>
  <span data-ttu-id="e78f1-103">캐시 변환은 데이터 흐름에 있는 연결된 데이터 원본의 데이터를 캐시 연결 관리자에 기록하여 조회 변환에 대한 참조 데이터 세트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="e78f1-103">The Cache Transform transformation generates a reference dataset for the Lookup Transformation by writing data from a connected data source in the data flow to a Cache connection manager.</span></span> <span data-ttu-id="e78f1-104">조회 변환은 연결된 데이터 원본의 입력 열에 있는 데이터를 참조 데이터베이스의 열과 조인하여 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="e78f1-104">The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in the reference database.</span></span>  
  
 <span data-ttu-id="e78f1-105">캐시 연결 관리자를 사용하여 조회 변환을 전체 캐시 모드로 실행하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78f1-105">You can use the Cache connection manager when you want to configure the Lookup Transformation to run in the full cache mode.</span></span> <span data-ttu-id="e78f1-106">이 모드에서 조회 변환이 실행되기 전에 참조 데이터 세트가 캐시에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="e78f1-106">In this mode, the reference dataset is loaded into cache before the Lookup Transformation runs.</span></span>  
  
 <span data-ttu-id="e78f1-107">캐시 연결 관리자 및 캐시 변환을 사용하여 전체 캐시 모드에서 조회 변환을 구성하는 방법에 대한 지침은 [캐시 연결 관리자 변환을 사용하여 전체 캐시 모드에서 조회 변환 구현](../../connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e78f1-107">For instructions on how to configure the Lookup transformation in full cache mode with the Cache connection manager and Cache Transform transformation, see [Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](../../connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="e78f1-108">참조 데이터 세트를 캐싱하는 방법은 [Lookup Transformation](lookup-transformation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e78f1-108">For more information on caching the reference dataset, see [Lookup Transformation](lookup-transformation.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e78f1-109">캐시 변환은 고유한 행만 캐시 연결 관리자에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="e78f1-109">The Cache Transform writes only unique rows to the Cache connection manager.</span></span>  
  
 <span data-ttu-id="e78f1-110">단일 패키지에서는 하나의 캐시 변환만 동일한 캐시 연결 관리자에 데이터를 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78f1-110">In a single package, only one Cache Transform can write data to the same Cache connection manager.</span></span> <span data-ttu-id="e78f1-111">패키지에 여러 캐시 변환이 포함된 경우에는 패키지가 실행될 때 호출되는 첫 번째 캐시 변환이 데이터를 연결 관리자에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="e78f1-111">If the package contains multiple Cache Transforms, the first Cache Transform that is called when the package runs, writes the data to the connection manager.</span></span> <span data-ttu-id="e78f1-112">이후 캐시 변환의 쓰기 작업은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e78f1-112">The write operations of subsequent Cache Transforms fail.</span></span>  
  
 <span data-ttu-id="e78f1-113">자세한 내용은 [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) 및 [Cache Connection Manager Editor](../../cache-connection-manager-editor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e78f1-113">For more information, see [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) and [Cache Connection Manager Editor](../../cache-connection-manager-editor.md).</span></span>  
  
## <a name="configuration-of-the-cache-transform"></a><span data-ttu-id="e78f1-114">캐시 변환 구성</span><span class="sxs-lookup"><span data-stu-id="e78f1-114">Configuration of the Cache Transform</span></span>  
 <span data-ttu-id="e78f1-115">데이터를 캐시 파일(.caw)에 저장하도록 캐시 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78f1-115">You can configure the Cache connection manager to save the data to a cache file (.caw).</span></span>  
  
 <span data-ttu-id="e78f1-116">다음과 같은 방법으로 캐시 변환을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78f1-116">You can configure the Cache Transform in the following ways:</span></span>  
  
-   <span data-ttu-id="e78f1-117">캐시 연결 관리자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e78f1-117">Specify the Cache connection manager.</span></span>  
  
-   <span data-ttu-id="e78f1-118">캐시 변환의 입력 열을 캐시 연결 관리자의 대상 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="e78f1-118">Map the input columns in the Cache Transform to destination columns in the Cache connection manager.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e78f1-119">각 입력 열은 대상 열로 매핑되어야 하며 열 데이터 형식이 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e78f1-119">Each input column must be mapped to a destination column, and the column data types must match.</span></span> <span data-ttu-id="e78f1-120">그렇지 않으면 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 디자이너에서 오류 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e78f1-120">Otherwise, [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Designer displays an error message.</span></span>  
  
     <span data-ttu-id="e78f1-121">**캐시 연결 관리자 편집기** 를 사용하여 열 데이터 형식, 이름 및 다른 열 속성을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78f1-121">You can use the **Cache Connection Manager Editor** to modify column data types, names, and other column properties.</span></span>  
  
 <span data-ttu-id="e78f1-122">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 디자이너에서 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78f1-122">You can set properties through [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Designer.</span></span> <span data-ttu-id="e78f1-123">**고급 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용은 [Transformation Custom Properties](transformation-custom-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e78f1-123">For more information about the properties that you can set in the **Advanced Editor** dialog box, see [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="e78f1-124">속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](../set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e78f1-124">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e78f1-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e78f1-125">See Also</span></span>  
 <span data-ttu-id="e78f1-126">[Integration Services 변환](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="e78f1-126">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 [<span data-ttu-id="e78f1-127">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="e78f1-127">Data Flow</span></span>](../data-flow.md)  
  
  
