---
title: XML 출력 파일 형식 (ssbdiagnose) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 612b317f7220f502faf1adc82cf9c1dcc8bc20a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735700"
---
# <a name="xml-output-file-format-ssbdiagnose"></a><span data-ttu-id="ef074-102">XML 출력 파일 형식(ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="ef074-102">XML Output File Format (ssbdiagnose)</span></span>
  <span data-ttu-id="ef074-103">**ssbdiagnose** 유틸리티는 **-XML** 스위치를 사용하여 실행하면 해당 출력을 XML 파일로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ef074-103">The **ssbdiagnose** utility delivers its output as an XML file when you run it with the **-XML** switch.</span></span> <span data-ttu-id="ef074-104">XML 출력 파일에는 헤더 정보와 분석된 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 구성 또는 대화에서 발견된 오류가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef074-104">The XML output file lists header information and the errors that it found in the [!INCLUDE[ssSB](../../includes/sssb-md.md)] configuration or conversation that was analyzed.</span></span> <span data-ttu-id="ef074-105">애플리케이션을 작성하여 이 파일에 나열된 오류를 분석하고 보고하거나</span><span class="sxs-lookup"><span data-stu-id="ef074-105">You can write an application to analyze or report on the errors listed in the file.</span></span> <span data-ttu-id="ef074-106">XML 메모장과 같은 일반적인 XML 편집기를 사용하여 이 XML 파일을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef074-106">Or, you can view the XML file in a general XML editor, such as XML Notepad.</span></span>  
  
 <span data-ttu-id="ef074-107">**ssbdiangose** 출력 파일에는 다음과 같은 두 개의 자식 유형이 있는 DiagnosticInformation 루트 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef074-107">An **ssbdiangose** output file contains a DiagnosticInformation root element with two child types:</span></span>  
  
-   <span data-ttu-id="ef074-108">헤더 정보가 있는 Banner 요소</span><span class="sxs-lookup"><span data-stu-id="ef074-108">A Banner element with header information.</span></span>  
  
-   <span data-ttu-id="ef074-109">**ssbdiagnose**가 보고하는 각 문제에 대한 Issue 요소</span><span class="sxs-lookup"><span data-stu-id="ef074-109">An Issue element for each issue that is reported by **ssbdiagnose**.</span></span>  
  
## <a name="diagnosticinformation-root-element"></a><span data-ttu-id="ef074-110">DiagnosticInformation 루트 요소</span><span class="sxs-lookup"><span data-stu-id="ef074-110">DiagnosticInformation Root Element</span></span>  
  
-   [<span data-ttu-id="ef074-111">DiagnosticInformation 요소&#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="ef074-111">DiagnosticInformation Element &#40;ssbdiagnose&#41;</span></span>](diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a><span data-ttu-id="ef074-112">Banner 요소</span><span class="sxs-lookup"><span data-stu-id="ef074-112">Banner Element</span></span>  
  
-   [<span data-ttu-id="ef074-113">Banner 요소&#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="ef074-113">Banner Element &#40;ssbdiagnose&#41;</span></span>](banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a><span data-ttu-id="ef074-114">Issue 요소</span><span class="sxs-lookup"><span data-stu-id="ef074-114">Issue Element</span></span>  
  
-   [<span data-ttu-id="ef074-115">Issue 요소&#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="ef074-115">Issue Element &#40;ssbdiagnose&#41;</span></span>](issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a><span data-ttu-id="ef074-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef074-116">See Also</span></span>  
 [<span data-ttu-id="ef074-117">ssbdiagnose 유틸리티&#40;Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="ef074-117">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](ssbdiagnose-utility-service-broker.md)  
  
  
