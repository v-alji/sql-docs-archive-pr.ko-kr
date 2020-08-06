---
title: 사용자 정의 멤버 속성 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- custom member properties [MDX]
ms.assetid: b64cc581-e784-42c4-bec8-932abd687423
author: minewiskan
ms.author: owend
ms.openlocfilehash: 75e5df5a0677ee205b5517f4c7ca89a390426971
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730956"
---
# <a name="user-defined-member-properties-mdx"></a><span data-ttu-id="a28ef-102">사용자 정의 멤버 속성(MDX)</span><span class="sxs-lookup"><span data-stu-id="a28ef-102">User-Defined Member Properties (MDX)</span></span>
  <span data-ttu-id="a28ef-103">사용자 정의 멤버 속성을 차원 내의 특정한 이름의 수준에 특성 관계로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a28ef-103">User-defined member properties can be added to a specific named level in a dimension as attribute relationships.</span></span> <span data-ttu-id="a28ef-104">계층의 `(All)` 수준 또는 수준 자체에는 사용자 정의 멤버 속성을 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a28ef-104">User-defined member properties cannot be added to the `(All)` level of a hierarchy, or to the hierarchy itself.</span></span>  
  
## <a name="creating-user-defined-member-properties"></a><span data-ttu-id="a28ef-105">사용자 정의 멤버 속성 만들기</span><span class="sxs-lookup"><span data-stu-id="a28ef-105">Creating User-Defined Member Properties</span></span>  
 <span data-ttu-id="a28ef-106">사용자 정의 멤버 속성을 서버 기반 차원 또는 큐브에 추가하는 데는 사용자 인터페이스 방식 또는 프로그래밍 방식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a28ef-106">User-defined member properties can be added to server-based dimensions or cubes either through the user interface or programmatically:</span></span>  
  
-   <span data-ttu-id="a28ef-107">사용자 인터페이스를 통해 사용자 정의 멤버 속성을 추가하려면 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]의 차원 디자이너를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="a28ef-107">To add user-defined member properties through the user interface, you use Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="a28ef-108">자세한 내용은 [특성 관계 정의](../attribute-relationships-define.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a28ef-108">For more information, see [Define Attribute Relationships](../attribute-relationships-define.md).</span></span>  
  
-   <span data-ttu-id="a28ef-109">프로그래밍 방식으로 사용자 정의 멤버 속성을 추가하려면 애플리케이션에서 AMO(Analysis Management Objects)를 사용하거나 XMLA(XML for Analysis) 및 ASSL(Analysis Services Scripting Language)을 조합하여 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="a28ef-109">To add user-defined member properties programmatically, your application can use either Analysis Manager Objects (AMO) or a combination of XML for Analysis (XMLA) and Analysis Services Scripting Language (ASSL).</span></span> <span data-ttu-id="a28ef-110">자세한 내용은 [특성 관계](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a28ef-110">For more information, see [Attribute Relationships](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
## <a name="retrieving-user-defined-member-properties"></a><span data-ttu-id="a28ef-111">사용자 정의 멤버 속성 검색</span><span class="sxs-lookup"><span data-stu-id="a28ef-111">Retrieving User-Defined Member Properties</span></span>  
 <span data-ttu-id="a28ef-112">`PROPERTIES`키워드 또는 [속성](/sql/mdx/properties-mdx) 함수를 사용 하 여 사용자 정의 멤버 속성을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a28ef-112">You can retrieve user-defined member properties using either the `PROPERTIES` keyword or the [Properties](/sql/mdx/properties-mdx) function.</span></span>  
  
### <a name="using-the-properties-keyword-to-retrieve-user-defined-member-properties"></a><span data-ttu-id="a28ef-113">PROPERTIES 키워드를 사용한 사용자 정의 멤버 속성 검색</span><span class="sxs-lookup"><span data-stu-id="a28ef-113">Using the PROPERTIES Keyword to Retrieve User-Defined Member Properties</span></span>  
 <span data-ttu-id="a28ef-114">사용자 정의 멤버 속성을 검색하는 구문은 다음 구문과 같이 기본 수준 멤버 속성을 검색하는 구문과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="a28ef-114">The syntax that retrieves user-defined member properties is similar to that used to retrieve intrinsic level member properties, as shown in the following syntax:</span></span>  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 <span data-ttu-id="a28ef-115">`PROPERTIES` 키워드는 축 사양의 집합 식 뒤에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a28ef-115">The `PROPERTIES` keyword appears after the set expression of the axis specification.</span></span> <span data-ttu-id="a28ef-116">예를 들어 다음 MDX 쿼리에는 1월에 판매된 제품을 식별하는 집합 식 뒤에 `List Price` 및 `Dealer Price` 사용자 정의 멤버 속성을 검색하는 `PROPERTIES` 키워드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a28ef-116">For example, the following MDX query the `PROPERTIES` keyword retrieves the `List Price` and `Dealer Price` user-defined member properties and appears after the set expression that identifies the products sold in January:</span></span>  
  
```  
SELECT   
   CROSSJOIN([Ship Date].[Calendar].[Calendar Year].Members,   
             [Measures].[Sales Amount]) ON COLUMNS,  
   NON EMPTY Product.Product.MEMBERS  
   DIMENSION PROPERTIES   
              Product.Product.[List Price],  
              Product.Product.[Dealer Price]  ON ROWS  
FROM [Adventure Works]  
WHERE ([Date].[Month of Year].[January])   
```  
  
### <a name="using-the-properties-function-to-retrieve-user-defined-member-properties"></a><span data-ttu-id="a28ef-117">Properties 함수를 사용하여 사용자 정의 멤버 속성 검색</span><span class="sxs-lookup"><span data-stu-id="a28ef-117">Using the Properties Function to Retrieve User-Defined Member Properties</span></span>  
 <span data-ttu-id="a28ef-118">또는 `Properties` 함수를 사용해 사용자 정의 멤버 속성에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a28ef-118">Alternatively, you can access custom member properties with the `Properties` function.</span></span> <span data-ttu-id="a28ef-119">예를 들어 다음 MDX 쿼리는 `WITH` 키워드를 사용해 `List Price` 멤버 속성으로 구성된 계산 멤버를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a28ef-119">For example, the following MDX query uses the `WITH` keyword to create a calculated member consisting of the `List Price` member property:</span></span>  
  
```  
WITH   
   MEMBER [Measures].[Product List Price] AS  
   [Product].[Product].CurrentMember.Properties("List Price")  
SELECT   
   [Measures].[Product List Price] on COLUMNS,  
   [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="a28ef-120">계산 멤버 작성에 대한 자세한 내용은 [계산 멤버를 MDX로 작성&#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a28ef-120">For more information about building calculated members, see [Building Calculated Members in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a28ef-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a28ef-121">See Also</span></span>  
 <span data-ttu-id="a28ef-122">[MDX&#41;&#40;멤버 속성 사용](mdx-member-properties.md) </span><span class="sxs-lookup"><span data-stu-id="a28ef-122">[Using Member Properties &#40;MDX&#41;](mdx-member-properties.md) </span></span>  
 [<span data-ttu-id="a28ef-123">속성&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="a28ef-123">Properties &#40;MDX&#41;</span></span>](/sql/mdx/properties-mdx)  
  
  
