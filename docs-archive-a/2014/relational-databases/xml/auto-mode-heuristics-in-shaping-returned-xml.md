---
title: 반환된 XML 모양 지정에서 AUTO 모드 추론 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, heuristics in shaping returned XML
ms.assetid: 6c5cb6c1-2921-4ba1-8100-0bf8074f9103
author: rothja
ms.author: jroth
ms.openlocfilehash: 7a64cda8989e1e45d4ad869f8883e1c9d65f4b7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646245"
---
# <a name="auto-mode-heuristics-in-shaping-returned-xml"></a><span data-ttu-id="7955d-102">반환된 XML 모양 지정에서 AUTO 모드 추론</span><span class="sxs-lookup"><span data-stu-id="7955d-102">AUTO Mode Heuristics in Shaping Returned XML</span></span>
  <span data-ttu-id="7955d-103">AUTO 모드는 쿼리를 기반으로 반환된 XML의 모양을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="7955d-103">AUTO mode determines the shape of returned XML based on the query.</span></span> <span data-ttu-id="7955d-104">요소 중첩 방법을 결정할 때 AUTO 모드 추론은 인접한 행의 열 값을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="7955d-104">In determining how elements are to be nested, AUTO mode heuristics compare column values in adjacent rows.</span></span> <span data-ttu-id="7955d-105">**ntext**, **text**, **image**및 **xml**을 제외한 모든 유형의 열이 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="7955d-105">Columns of all types, except **ntext**, **text**, **image**, and **xml**, are compared.</span></span> <span data-ttu-id="7955d-106">**(n)varchar(max)** 및 **varbinary(max)** 유형의 열이 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="7955d-106">Columns of type **(n)varchar(max)** and **varbinary(max)** are compared.</span></span>  
  
 <span data-ttu-id="7955d-107">다음 예에서는 결과 XML의 모양을 결정하는 AUTO 모드 추론에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7955d-107">The following example illustrates the AUTO mode heuristics that determine the shape of the resulting XML:</span></span>  
  
```  
SELECT T1.Id, T2.Id, T1.Name  
FROM   T1, T2  
WHERE ...  
FOR XML AUTO  
ORDER BY T1.Id  
```  
  
 <span data-ttu-id="7955d-108">테이블 T1의 키가 지정되지 않은 경우 새로운 <`T1`> 요소가 시작되는 위치를 확인하기 위해 **ntext**, **text**, **image** 및 **xml**을 제외한 T1의 모든 열 값이 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="7955d-108">To determine where a new <`T1`> element starts, all column values of T1, except **ntext**, **text**, **image** and **xml**, are compared if the key on the table T1 is not specified.</span></span> <span data-ttu-id="7955d-109">그런 다음 **Name** 열이 **nvarchar(40)** 이고 SELECT 문이 이 행 집합을 반환한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="7955d-109">Next, assume that the **Name** column is **nvarchar(40)** and the SELECT statement returns this rowset:</span></span>  
  
```  
T1.Id  T1.Name  T2.Id  
-----------------------  
1       Andrew    2  
1       Andrew    3  
1       Nancy     4  
```  
  
 <span data-ttu-id="7955d-110">AUTO 모드 추론은 테이블 T1, Id 및 Name 열의 모든 값을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="7955d-110">The AUTO mode heuristics compare all the values of table T1, the Id and Name columns.</span></span> <span data-ttu-id="7955d-111">처음 두 행은 Id 및 Name 열에 대한 값이 같기 때문에 두 개의 \<T2> 자식 요소가 포함된 하나의 \<T1> 요소가 결과에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="7955d-111">Because the first two rows have the same values for the Id and Name columns, one \<T1> element having two \<T2> child elements is added in the result.</span></span>  
  
 <span data-ttu-id="7955d-112">다음은 반환되는 XML입니다.</span><span class="sxs-lookup"><span data-stu-id="7955d-112">Following is the XML that is returned:</span></span>  
  
```  
<T1 Id="1" Name="Andrew">  
    <T2 Id="2" />  
    <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
      <T2 Id="4" />  
</T>  
```  
  
 <span data-ttu-id="7955d-113">이제 Name 열이 **text** 유형이라고 가정해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="7955d-113">Now assume that the Name column is of **text** type.</span></span> <span data-ttu-id="7955d-114">AUTO 모드 추론은 이 유형의 값을 비교하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7955d-114">The AUTO mode heuristics do not compare the values for this type.</span></span> <span data-ttu-id="7955d-115">그 대신 값이 같지 않다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="7955d-115">Instead, it assumes that the values are not the same.</span></span> <span data-ttu-id="7955d-116">그 결과 다음과 같이 XML이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7955d-116">This results in XML generation as shown in the following:</span></span>  
  
```  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="2" />  
</T1>  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
  <T2 Id="4" />  
</T1>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7955d-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7955d-117">See Also</span></span>  
 [<span data-ttu-id="7955d-118">FOR XML에서 AUTO 모드 사용</span><span class="sxs-lookup"><span data-stu-id="7955d-118">Use AUTO Mode with FOR XML</span></span>](use-auto-mode-with-for-xml.md)  
  
  
