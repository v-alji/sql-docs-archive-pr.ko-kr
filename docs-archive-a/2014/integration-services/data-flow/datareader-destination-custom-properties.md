---
title: DataReader 대상 사용자 지정 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 62b6f628614d533e1bebcce071ce4761e73e08f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651816"
---
# <a name="datareader-destination-custom-properties"></a><span data-ttu-id="6f320-102">DataReader 대상 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="6f320-102">DataReader Destination Custom Properties</span></span>
  <span data-ttu-id="6f320-103">DataReader 대상에는 사용자 지정 속성과 모든 데이터 흐름 구성 요소에 공통된 속성이 모두 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f320-103">The DataReader destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="6f320-104">다음 표에서는 DataReader 대상의 사용자 지정 속성을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6f320-104">The following table describes the custom properties of the DataReader destination.</span></span> <span data-ttu-id="6f320-105">`DataReader`를 제외한 모든 속성은 읽기/쓰기가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="6f320-105">All properties except for `DataReader` are read/write.</span></span>  
  
|<span data-ttu-id="6f320-106">속성 이름</span><span class="sxs-lookup"><span data-stu-id="6f320-106">Property name</span></span>|<span data-ttu-id="6f320-107">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="6f320-107">Data Type</span></span>|<span data-ttu-id="6f320-108">Description</span><span class="sxs-lookup"><span data-stu-id="6f320-108">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="6f320-109">DataReader</span><span class="sxs-lookup"><span data-stu-id="6f320-109">DataReader</span></span>|<span data-ttu-id="6f320-110">String</span><span class="sxs-lookup"><span data-stu-id="6f320-110">String</span></span>|<span data-ttu-id="6f320-111">DataReader 대상의 클래스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6f320-111">The class name of the DataReader destination.</span></span>|  
|<span data-ttu-id="6f320-112">FailOnTimeout</span><span class="sxs-lookup"><span data-stu-id="6f320-112">FailOnTimeout</span></span>|<span data-ttu-id="6f320-113">부울</span><span class="sxs-lookup"><span data-stu-id="6f320-113">Boolean</span></span>|<span data-ttu-id="6f320-114">`ReadTimeout`이 발생하는 경우의 실패 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6f320-114">Indicates whether to fail when a `ReadTimeout` occurs.</span></span> <span data-ttu-id="6f320-115">이 속성의 기본값은 **False**입니다.</span><span class="sxs-lookup"><span data-stu-id="6f320-115">The default value of this property is **False**.</span></span>|  
|<span data-ttu-id="6f320-116">ReadTimeout</span><span class="sxs-lookup"><span data-stu-id="6f320-116">ReadTimeout</span></span>|<span data-ttu-id="6f320-117">정수</span><span class="sxs-lookup"><span data-stu-id="6f320-117">Integer</span></span>|<span data-ttu-id="6f320-118">시간이 초과되기 전의 시간(밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="6f320-118">The number of milliseconds before a time-out occurs.</span></span> <span data-ttu-id="6f320-119">이 속성의 기본값은 30000(30초)입니다.</span><span class="sxs-lookup"><span data-stu-id="6f320-119">The default value of this property is 30000 (30 seconds).</span></span>|  
  
 <span data-ttu-id="6f320-120">DataReader 대상의 입력 및 입력 열에는 사용자 지정 속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f320-120">The input and the input columns of the DataReader destination have no custom properties.</span></span>  
  
 <span data-ttu-id="6f320-121">자세한 내용은 [DataReader Destination](datareader-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f320-121">For more information, see [DataReader Destination](datareader-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f320-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f320-122">See Also</span></span>  
 [<span data-ttu-id="6f320-123">Common Properties</span><span class="sxs-lookup"><span data-stu-id="6f320-123">Common Properties</span></span>](../common-properties.md)  
  
  
