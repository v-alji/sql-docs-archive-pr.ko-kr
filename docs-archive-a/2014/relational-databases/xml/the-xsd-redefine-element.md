---
title: '&lt;xsd:redefine&gt; 요소 | Microsoft 문서'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xsd:redefine element
ms.assetid: 5f3e9b65-f10e-4db2-a62c-b270ac11d04e
author: rothja
ms.author: jroth
ms.openlocfilehash: ce439e81cf87e97b4afe6e25a201e1ab0cb2a458
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735131"
---
# <a name="the-ltxsdredefinegt-element"></a><span data-ttu-id="1978c-102">&lt;xsd:redefine&gt; 요소</span><span class="sxs-lookup"><span data-stu-id="1978c-102">The &lt;xsd:redefine&gt; Element</span></span>
  <span data-ttu-id="1978c-103">W3C XSD **redefine** 요소를 사용하면 스키마 구성 요소를 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1978c-103">The W3C XSD **redefine** element provides support for redefining schema components.</span></span> <span data-ttu-id="1978c-104">그러나이 지시문에 대 한 지원은 성능이 저하 될 수 있으며 다시 정의 된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `xml` 스키마와 연결 된 데이터 형식의 모든 인스턴스에 대해 유효성을 다시 검사 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1978c-104">However, support for this directive is potentially costly to performance and also requires that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] revalidate all instances of the `xml` data type associated with the redefined schema.</span></span> <span data-ttu-id="1978c-105">따라서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 이 요소를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1978c-105">Therefore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not support this element.</span></span> <span data-ttu-id="1978c-106">**\<xsd:redefine>** 요소를 포함하는 XML 스키마는 서버에서 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="1978c-106">XML schemas that include the **\<xsd:redefine>** element are rejected by the server.</span></span>  
  
 <span data-ttu-id="1978c-107">스키마나 해당 구성 요소를 업데이트하려면 대신 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="1978c-107">To update a schema or its components, you can do the following instead:</span></span>  
  
1.  <span data-ttu-id="1978c-108">수정한 스키마 구성 요소를 사용하여 XML 스키마 컬렉션을 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1978c-108">Create a new XML Schema collection with the modified schema components.</span></span>  
  
2.  <span data-ttu-id="1978c-109">새 XML 스키마 컬렉션을 대신 사용하도록 다시 정의되기 위해 XML 스키마 컬렉션을 사용하는 모든 `xml` 데이터 형식(XML DT)을 다시 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1978c-109">Retype all `xml` data types (XML DT) that use the XML Schema collection to be redefined to use the new XML Schema collection instead.</span></span> <span data-ttu-id="1978c-110">이 작업을 수행하려면 ALTER TABLE 명령의 ALTER COLUMN 옵션을 사용하여 열을 다시 입력하거나 변수나 매개 변수에 XML 스키마 컬렉션 제약 조건을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1978c-110">To do this, use the ALTER COLUMN option of the ALTER TABLE command for retyping columns, or change the XML Schema collection constraints on variables or parameters.</span></span>  
  
3.  <span data-ttu-id="1978c-111">XML 스키마 컬렉션의 이전 버전을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="1978c-111">Drop the old version of the XML Schema collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1978c-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1978c-112">See Also</span></span>  
 [<span data-ttu-id="1978c-113">서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="1978c-113">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
