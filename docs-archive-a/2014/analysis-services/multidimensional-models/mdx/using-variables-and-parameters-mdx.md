---
title: 변수 및 매개 변수 사용 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- parameters [MDX]
- queries [MDX], variables
- queries [MDX], parameters
- variables [MDX]
ms.assetid: a4754d16-d9c4-49f6-9be0-392180b912e4
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd01cf78ea5e3284aa51cad7dc848176a5dc9298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736988"
---
# <a name="using-variables-and-parameters-mdx"></a><span data-ttu-id="795a1-102">변수 및 매개 변수 사용(MDX)</span><span class="sxs-lookup"><span data-stu-id="795a1-102">Using Variables and Parameters (MDX)</span></span>
  <span data-ttu-id="795a1-103">에서는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] MDX (Multidimensional Expressions) 문을 매개 변수화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="795a1-103">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], you can parameterize a Multidimensional Expressions (MDX) statement.</span></span> <span data-ttu-id="795a1-104">매개 변수가 있는 문을 사용하면 런타임에 사용자 정의가 가능한 범용 문을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="795a1-104">A parameterized statement lets you create generic statements that can be customized at runtime.</span></span>  
  
 <span data-ttu-id="795a1-105">매개 변수가 있는 문을 만들 때 매개 변수 이름은 이름 앞에 @ 부호를 붙여 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="795a1-105">In creating a parameterized statement, you identify the parameter name by prefixing the name with the at sign (@).</span></span> <span data-ttu-id="795a1-106">예를 들어는 @Year 유효한 매개 변수 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="795a1-106">For example, @Year would be a valid parameter name</span></span>  
  
 <span data-ttu-id="795a1-107">MDX는 리터럴 또는 스칼라 값을 위한 매개 변수만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="795a1-107">MDX supports only parameters for literal or scalar values.</span></span> <span data-ttu-id="795a1-108">멤버, 집합 또는 튜플을 참조하는 매개 변수를 만들려면 [StrToMember](/sql/mdx/strtomember-mdx) 또는 [StrToSet](/sql/mdx/strtoset-mdx)와 같은 함수를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="795a1-108">To create a parameter that references a member, set, or tuple, you would have to use a function such as [StrToMember](/sql/mdx/strtomember-mdx) or [StrToSet](/sql/mdx/strtoset-mdx).</span></span>  
  
 <span data-ttu-id="795a1-109">다음 XML for Analysis (XMLA) 예에서 @CountryName 매개 변수는 고객 데이터가 검색 되는 국가를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="795a1-109">In the following XML for Analysis (XMLA) example, the @CountryName parameter will contain the country for which customer data is retrieved:</span></span>  
  
```  
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">  
  <Body>  
    <Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <Command>  
        <Statement>  
select [Measures].members on 0,   
       Filter(Customer.[Customer Geography].Country.members,   
              Customer.[Customer Geography].CurrentMember.Name =  
              @CountryName) on 1  
from [Adventure Works]  
</Statement>  
      </Command>  
      <Properties />  
      <Parameters>  
        <Parameter>  
          <Name>CountryName</Name>  
          <Value>'United Kingdom'</Value>  
        </Parameter>  
      </Parameters>  
    </Execute>  
  </Body>  
</Envelope>  
```  
  
 <span data-ttu-id="795a1-110">OLE DB와 함께 이 기능을 사용하려면 `ICommandWithParameters` 인터페이스를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="795a1-110">To use this functionality with OLE DB, you would use the `ICommandWithParameters` interface.</span></span> <span data-ttu-id="795a1-111">ADOMD.Net과 함께 이 기능을 사용하려면 **AdomdCommand.Parameters** 컬렉션을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="795a1-111">To use this functionality with ADOMD.Net, you would use the **AdomdCommand.Parameters** collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="795a1-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="795a1-112">See Also</span></span>  
 [<span data-ttu-id="795a1-113">MDX 스크립팅 기본 사항&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="795a1-113">MDX Scripting Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-scripting-fundamentals-analysis-services.md)  
  
  
