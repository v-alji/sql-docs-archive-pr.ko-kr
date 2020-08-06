---
title: 레코드 집합 대상 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.recordsetdest.f1
helpviewer_keywords:
- Recordset destination
- ADO recordsets [Integration Services]
- destinations [Integration Services], Recordset
- in-memory ADO recordsets [Integration Services]
ms.assetid: be973cf1-c4ff-49f8-987e-314c08ef98e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1acc29c904e9020721e8ac62dff09a8ec29a392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648453"
---
# <a name="recordset-destination"></a><span data-ttu-id="ebca2-102">레코드 집합 대상</span><span class="sxs-lookup"><span data-stu-id="ebca2-102">Recordset Destination</span></span>
  <span data-ttu-id="ebca2-103">레코드 집합 대상은 메모리 내 ADO 레코드 집합을 만들고 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="ebca2-103">The Recordset destination creates and populates an in-memory ADO recordset.</span></span> <span data-ttu-id="ebca2-104">레코드 집합의 모양은 디자인 타임에 레코드 집합 대상에 대한 입력에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebca2-104">The shape of the recordset is defined by the input to the Recordset destination at design time.</span></span>  
  
## <a name="configuration-of-the-recordset-destination"></a><span data-ttu-id="ebca2-105">레코드 집합 대상 구성</span><span class="sxs-lookup"><span data-stu-id="ebca2-105">Configuration of the Recordset Destination</span></span>  
 <span data-ttu-id="ebca2-106">레코드 집합 대상은 ADO 레코드 집합에 저장되는 변수를 지정하여 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebca2-106">You configure the Recordset destination by specifying the variable that stores the ADO recordset.</span></span>  
  
 <span data-ttu-id="ebca2-107">런타임 시 ADO 레코드 집합은 레코드 집합 대상의 VariableName 속성에 지정된 개체 유형의 변수에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebca2-107">At run time, an ADO recordset is written to the variable of type, Object, that is specified in the VariableName property of the Recordset destination.</span></span> <span data-ttu-id="ebca2-108">그런 다음 이 변수를 통해 데이터 흐름 외부의 스크립트 및 다른 패키지 요소에서 레코드 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebca2-108">The variable then makes the Recordset available outside the data flow, where it can be used by scripts and other package elements.</span></span>  
  
 <span data-ttu-id="ebca2-109">이 원본에는 하나의 입력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebca2-109">This source has one input.</span></span> <span data-ttu-id="ebca2-110">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebca2-110">It does not support an error output.</span></span>  
  
 <span data-ttu-id="ebca2-111">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebca2-111">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="ebca2-112">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebca2-112">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="ebca2-113">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="ebca2-113">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ebca2-114">Common Properties</span><span class="sxs-lookup"><span data-stu-id="ebca2-114">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="ebca2-115">레코드 집합 대상 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="ebca2-115">Recordset Destination Custom Properties</span></span>](recordset-destination-custom-properties.md)  
  
 <span data-ttu-id="ebca2-116">속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebca2-116">For more information about how to set the properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="ebca2-117">관련 작업</span><span class="sxs-lookup"><span data-stu-id="ebca2-117">Related Tasks</span></span>  
 [<span data-ttu-id="ebca2-118">레코드 집합 대상 사용</span><span class="sxs-lookup"><span data-stu-id="ebca2-118">Use a Recordset Destination</span></span>](recordset-destination.md)  
  
  
