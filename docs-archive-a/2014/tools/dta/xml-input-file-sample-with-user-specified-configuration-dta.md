---
title: 사용자 지정 구성이 포함된 XML 입력 파일 샘플(DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- sample applications [DTA]
ms.assetid: b29c9716-e5c3-4003-9efb-3ade2197b630
author: stevestein
ms.author: sstein
ms.openlocfilehash: 121972518aa114e16cc81517d52a9d9656b067c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653084"
---
# <a name="xml-input-file-sample-with-user-specified-configuration-dta"></a><span data-ttu-id="ba28d-102">사용자 지정 구성이 포함된 XML 입력 파일 예제(DTA)</span><span class="sxs-lookup"><span data-stu-id="ba28d-102">XML Input File Sample with User-specified Configuration (DTA)</span></span>
  <span data-ttu-id="ba28d-103">**Configuration** 요소를 사용하여 사용자 지정 구성을 지정하는 이 XML 입력 파일 예제를 복사하여 좋아하는 XML 편집기나 텍스트 편집기에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ba28d-103">Copy and paste this sample of an XML input file that specifies a user-specified configuration with the **Configuration** element into your favorite XML editor or text editor.</span></span> <span data-ttu-id="ba28d-104">이렇게 하면 "가정(what-if)" 분석을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba28d-104">This enables you to perform "what-if" analysis.</span></span> <span data-ttu-id="ba28d-105">"가정(what-if)" 분석에는 **Configuration** 요소를 사용하여 튜닝할 데이터베이스에 대한 가상 실제 디자인 구조 집합을 지정하는 것이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba28d-105">"What-if" analysis involves using the **Configuration** element to specify a set of hypothetical physical design structures for the database you want to tune.</span></span> <span data-ttu-id="ba28d-106">그런 다음 데이터베이스 엔진 튜닝 관리자를 사용하여 이 가상 구성에 대해 작업을 실행하는 것의 효과를 분석하여 쿼리 처리 성능을 향상시키는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ba28d-106">Then you use Database Engine Tuning Advisor to analyze the effects of running a workload against this hypothetical configuration to find out whether it improves query processing performance.</span></span> <span data-ttu-id="ba28d-107">이 분석 유형은 실제 구현 시 오버헤드를 발생시키지 않고 새 구성을 평가하는 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba28d-107">This type of analysis provides the advantage of evaluating the new configuration without incurring the overhead of actually implementing it.</span></span> <span data-ttu-id="ba28d-108">가상 구성이 원하는 성능 향상을 제공하지 않을 경우 필요한 결과를 달성하는 구성에 도달할 때까지 가상 구성을 쉽게 변경하여 다시 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba28d-108">If your hypothetical configuration does not provide the performance improvements you want, it is easy to change it and analyze it again until you reach the configuration that produces the results you need.</span></span>  
  
 <span data-ttu-id="ba28d-109">이 예제를 편집 도구에 복사한 후에 **Server**, **Database**, **Schema**, **Table**, **Workload**, **TuningOptions**및 **Configuration** 요소에 지정된 값을 특정 튜닝 세션에 대한 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ba28d-109">After copying this sample into your editing tool, replace the values specified for the **Server**, **Database**, **Schema**, **Table**, **Workload**, **TuningOptions**, and **Configuration** elements with those for your specific tuning session.</span></span> <span data-ttu-id="ba28d-110">이러한 요소에 사용할 수 있는 모든 특성 및 자식 요소에 대한 자세한 내용은 [XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ba28d-110">For more information about all of the attributes and child elements that you can use with these elements, see the [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md).</span></span> <span data-ttu-id="ba28d-111">다음 예에서는 사용 가능한 특성 및 자식 요소 옵션의 하위 집합만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ba28d-111">The following sample uses only a subset of available attribute and child element options.</span></span>  
  
## <a name="code"></a><span data-ttu-id="ba28d-112">코드</span><span class="sxs-lookup"><span data-stu-id="ba28d-112">Code</span></span>  
 [!code-xml[InputFileSamples#UserSpecifiedConfigInputFile](../../snippets/xml/SQL14/dta_xml/inputfilesamples/xml/dta_xml_input_file_samples.xml#userspecifiedconfiginputfile)]  
  
## <a name="comments"></a><span data-ttu-id="ba28d-113">주석</span><span class="sxs-lookup"><span data-stu-id="ba28d-113">Comments</span></span>  
  
-   <span data-ttu-id="ba28d-114">**Configuration** 요소에 대해 **Absolute** 모드를 지정할 경우(`Configuration SpecificationMode="Absolute"`) 실제 디자인 구조의 삭제는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ba28d-114">Dropping physical design structures is not supported if you specify the **Absolute** mode for the **Configuration** element (`Configuration SpecificationMode="Absolute"`).</span></span>  
  
-   <span data-ttu-id="ba28d-115">**Configuration** 요소의 두 모드( **Relative**또는 **Absolute** )에서 모두 동일한 실제 디자인 구조를 만들고 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ba28d-115">You cannot create and drop the same physical design structure in either mode (**Relative** or **Absolute**) of the **Configuration** element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba28d-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba28d-116">See Also</span></span>  
 <span data-ttu-id="ba28d-117">[데이터베이스 엔진 튜닝 관리자 시작 및 사용](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="ba28d-117">[Start and Use the Database Engine Tuning Advisor](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md) </span></span>  
 <span data-ttu-id="ba28d-118">[데이터베이스 엔진 튜닝 관리자의 출력 보기 및 작업](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="ba28d-118">[View and Work with the Output from the Database Engine Tuning Advisor](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md) </span></span>  
 [<span data-ttu-id="ba28d-119">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="ba28d-119">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
