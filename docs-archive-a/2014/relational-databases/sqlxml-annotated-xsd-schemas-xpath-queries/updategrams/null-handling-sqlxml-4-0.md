---
title: NULL 처리 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updg:nullvalue attribute
- updategrams [SQLXML], null values
- nullvalue attribute
- null values [SQLXML]
ms.assetid: 5e11eebb-d94e-4ce6-a6d0-870225706bc1
author: rothja
ms.author: jroth
ms.openlocfilehash: 430643e8a6c9bd3dd00b2763990645c6a162ee40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652742"
---
# <a name="null-handling-sqlxml-40"></a><span data-ttu-id="44212-102">NULL 처리(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="44212-102">NULL Handling (SQLXML 4.0)</span></span>
  <span data-ttu-id="44212-103">XML 구문에서는 NULL을 부재로 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="44212-103">XML syntax denotes NULL as an absence.</span></span> <span data-ttu-id="44212-104">예를 들어 특성 또는 요소 값이 NULL 이면 해당 특성이 나 요소가 XML 문서에 없는 것입니다. [!INCLUDE[msCoName](../../../includes/msconame-md.md)]SQLXML에서는 특성을 사용 하 여 `updg:nullvalue` 요소 또는 특성 값에 NULL을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44212-104">(For example, if an attribute or element value is NULL, that attribute or element is absent from the XML document.) In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML, the `updg:nullvalue` attribute enables specifying NULL for an element or attribute value.</span></span>  
  
 <span data-ttu-id="44212-105">예를 들어 다음 updategram은 **ContactID** 가 64 인 연락처의 **TITLE** 값이 NULL 인지 확인 하 고 **title** 값을 "Mr"로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="44212-105">For example, the following updategram ensures that the **Title** value for a contact with **ContactID** of 64 is NULL, and then updates the **Title** value to "Mr."</span></span> <span data-ttu-id="44212-106">업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="44212-106">for this contact.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync updg:nullvalue="IsNULL"  >  
    <updg:before>  
       <Person.Contact ContactID="64" Title="IsNULL" />  
    </updg:before>  
    <updg:after>  
       <Person.Contact ContactID="64" Title="Mr." />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="44212-107">매개 변수가 Updategram으로 전달되는 경우 NULL도 매개 변수 값으로 전달될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44212-107">When parameters are passed to an updategram, NULL can be passed as the parameter value.</span></span> <span data-ttu-id="44212-108">이 작업을 수행하려면 `nullvalue` 블록에 `<updg:header>` 특성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="44212-108">This is done by specifying the `nullvalue` attribute in the `<updg:header>` block.</span></span> <span data-ttu-id="44212-109">예제는 [Updategrams &#40;SQLXML 4.0&#41;에 매개 변수 전달 ](passing-parameters-to-updategrams-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="44212-109">For an example, see [Passing Parameters to Updategrams &#40;SQLXML 4.0&#41;](passing-parameters-to-updategrams-sqlxml-4-0.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44212-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="44212-110">See Also</span></span>  
 [<span data-ttu-id="44212-111">Updategram 보안 고려 사항은 SQLXML 4.0&#41;&#40;</span><span class="sxs-lookup"><span data-stu-id="44212-111">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
