---
title: 인라인 작업이 포함된 XML 입력 파일 샘플(DTA) | Microsoft Docs
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
ms.assetid: 7c04fe1d-6669-44a1-8b73-36d469e9b002
author: stevestein
ms.author: sstein
ms.openlocfilehash: 93b2ab4279378b4cd392d97a9b65f299d0e9c6dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649288"
---
# <a name="xml-input-file-sample-with-inline-workload-dta"></a><span data-ttu-id="e3dfb-102">인라인 작업이 포함된 XML 입력 파일 예제(DTA)</span><span class="sxs-lookup"><span data-stu-id="e3dfb-102">XML Input File Sample with Inline Workload (DTA)</span></span>
  <span data-ttu-id="e3dfb-103">**EventString** 요소를 사용하여 작업을 지정하는 XML 입력 파일의 이 예제를 복사한 다음 자주 사용하는 XML 편집기나 텍스트 편집기에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="e3dfb-103">Copy and paste this sample of an XML input file that specifies a workload with the **EventString** element into your favorite XML editor or text editor.</span></span> <span data-ttu-id="e3dfb-104">**EventString** 요소를 사용하면 별개의 작업 파일을 사용하는 대신에 XML 입력 파일에 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 작업을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3dfb-104">You can use the **EventString** element to specify a [!INCLUDE[tsql](../../includes/tsql-md.md)] script workload in the XML input file instead of using a separate workload file.</span></span> <span data-ttu-id="e3dfb-105">이 예제를 편집 도구에 복사한 후에 **Server**, **Database**, **Schema**, **Table**, **Workload**, **EventString**및 **TuningOptions** 요소에 지정된 값을 특정 튜닝 세션에 대한 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e3dfb-105">After copying this sample into your editing tool, replace the values specified for the **Server**, **Database**, **Schema**, **Table**, **Workload**, **EventString**, and **TuningOptions** elements with those for your specific tuning session.</span></span> <span data-ttu-id="e3dfb-106">이러한 요소에 사용할 수 있는 모든 특성 및 자식 요소에 대한 자세한 내용은 [XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e3dfb-106">For more information about all of the attributes and child elements that you can use with these elements, see the [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md).</span></span> <span data-ttu-id="e3dfb-107">다음 예에서는 사용 가능한 특성 및 자식 요소 옵션의 하위 집합만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e3dfb-107">The following sample uses only a subset of available attribute and child element options.</span></span>  
  
## <a name="code"></a><span data-ttu-id="e3dfb-108">코드</span><span class="sxs-lookup"><span data-stu-id="e3dfb-108">Code</span></span>  
 [!code-xml[InputFileSamples#InlineWorkloadInputFile](../../snippets/xml/SQL14/dta_xml/inputfilesamples/xml/dta_xml_input_file_samples.xml#inlineworkloadinputfile)]  
  
## <a name="comments"></a><span data-ttu-id="e3dfb-109">주석</span><span class="sxs-lookup"><span data-stu-id="e3dfb-109">Comments</span></span>  
 <span data-ttu-id="e3dfb-110">`USE database_name` EventString **요소에 포함된 인라인 작업에서** 문을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3dfb-110">`USE database_name` statements can be specified in the inline workload that is contained in the **EventString** element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3dfb-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3dfb-111">See Also</span></span>  
 <span data-ttu-id="e3dfb-112">[데이터베이스 엔진 튜닝 관리자 시작 및 사용](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="e3dfb-112">[Start and Use the Database Engine Tuning Advisor](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md) </span></span>  
 <span data-ttu-id="e3dfb-113">[데이터베이스 엔진 튜닝 관리자의 출력 보기 및 작업](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="e3dfb-113">[View and Work with the Output from the Database Engine Tuning Advisor](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md) </span></span>  
 [<span data-ttu-id="e3dfb-114">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="e3dfb-114">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
