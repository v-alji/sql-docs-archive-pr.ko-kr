---
title: 새&#39;s (Integration Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, what's new
- what's new [Integration Services]
ms.assetid: da6999c7-e5e3-4a59-a284-1da635995af1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 84f0b668407c89e1d6acc3c8cfbda73f129ca19a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660028"
---
# <a name="what39s-new-integration-services"></a><span data-ttu-id="28b03-102">새&#39;s (Integration Services)</span><span class="sxs-lookup"><span data-stu-id="28b03-102">What&#39;s New (Integration Services)</span></span>
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="28b03-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]는 이전 릴리스에서 변경 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="28b03-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] is unchanged from the previous release.</span></span>  
  
 <span data-ttu-id="28b03-104">다른 제품 및 기술에 대 한 자세한 내용은 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [SQL Server 2014의 새로운 기능](../sql-server/what-s-new-in-sql-server-2016.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28b03-104">For information about other [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] products and technologies, see [What's New in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).</span></span>  
  
 <span data-ttu-id="28b03-105">비즈니스 인텔리전스와 관련 된 변경 내용에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Analysis Services 및 비즈니스 인텔리전스의 새로운 기능](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28b03-105">For more information about changes related to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence, see [What's New in Analysis Services and Business Intelligence](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services).</span></span>  
  
##  <a name="rich-xml-validation-output-in-the-xml-task"></a><a name="ValidateXML"></a> <span data-ttu-id="28b03-106">XML 태스크에서 풍부한 XML 유효성 검사 출력</span><span class="sxs-lookup"><span data-stu-id="28b03-106">Rich XML validation output in the XML Task</span></span>  
 <span data-ttu-id="28b03-107">XML 태스크의 `ValidationDetails` 속성을 사용하도록 설정하여 XML 문서의 유효성을 검사하고 풍부한 오류 출력을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28b03-107">Validate XML documents and get rich error output by enabling the `ValidationDetails` property of the XML Task.</span></span> <span data-ttu-id="28b03-108">`ValidationDetails` 속성을 사용할 수 있게 되기 전에 먼저 XML 태스크에 의해 수행된 XML 유효성 검사가 오류 또는 해당 위치에 대한 정보 없이 true 또는 false 결과만 반환했습니다.</span><span class="sxs-lookup"><span data-stu-id="28b03-108">Before the `ValidationDetails` property was available, XML validation by the XML Task returned only a true or false result, with no information about errors or their locations.</span></span> <span data-ttu-id="28b03-109">이제 `ValidationDetails`를 true로 설정할 경우 출력 파일에는 줄 번호 및 위치를 포함하여 모든 오류에 대한 자세한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="28b03-109">Now, when you set `ValidationDetails` to true, the output file contains detailed information about every error including the line number and the position.</span></span> <span data-ttu-id="28b03-110">이 정보를 사용하여 XML 문서의 오류를 이해하고, 찾고, 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28b03-110">You can use this information to understand, locate, and fix errors in XML documents.</span></span> <span data-ttu-id="28b03-111">자세한 내용은 [Validate XML with the XML Task](control-flow/xml-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="28b03-111">For more info, see [Validate XML with the XML Task](control-flow/xml-task.md).</span></span>  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)]<span data-ttu-id="28b03-112">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 서비스 팩 2에는 `ValidationDetails` 속성이 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="28b03-112">introduced the `ValidationDetails` property in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 2.</span></span> <span data-ttu-id="28b03-113">이 새 속성은 당시에는 발표되거나 문서화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="28b03-113">This new property was not announced or documented at that time.</span></span> <span data-ttu-id="28b03-114">`ValidationDetails` 속성 또한 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 및 SQL Server 2016에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28b03-114">The `ValidationDetails` property is also available in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] and in SQL Server 2016.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28b03-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="28b03-115">See Also</span></span>  
 [<span data-ttu-id="28b03-116">SQL Server 2014 버전에서 지원하는 기능</span><span class="sxs-lookup"><span data-stu-id="28b03-116">Features Supported by the Editions of SQL Server 2014</span></span>](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
