---
title: 인라인 XDR 스키마 생성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XDR schemas [SQL Server]
- inline XDR schema generation [SQL Server]
- XMLDATA option
- FOR XML clause, inline XDR schema generation
ms.assetid: 2a40d617-9724-4f7d-80a4-a85c702f14d0
author: rothja
ms.author: jroth
ms.openlocfilehash: 0e2bb7b4b482b79ab5550540dd5b24ffdd8d6636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743075"
---
# <a name="generate-an-inline-xdr-schema"></a><span data-ttu-id="707ad-102">인라인 XDR 스키마 생성</span><span class="sxs-lookup"><span data-stu-id="707ad-102">Generate an Inline XDR Schema</span></span>
  <span data-ttu-id="707ad-103">FOR XML의 **XMLDATA** 지시어는 쿼리 결과와 함께 인라인 XDR 스키마를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="707ad-103">The **XMLDATA** directive in FOR XML returns an inline XDR schema together with the query result.</span></span> <span data-ttu-id="707ad-104">하지만 XDR 스키마는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서 제공되는 새로운 데이터 형식과 기타 향상된 기능 중 일부를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="707ad-104">However, the XDR schema does not support all the new data types and other enhancements introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="707ad-105">대신 [XMLSCHEMA](generate-an-inline-xsd-schema.md)지시어를 사용하여 인라인 XSD 스키마를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="707ad-105">Instead, you can request an inline XSD schema by using [the XMLSCHEMA directive](generate-an-inline-xsd-schema.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="707ad-106">XMLDATA 지시어에 FOR XML 옵션은 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="707ad-106">The XMLDATA directive to the FOR XML option is deprecated.</span></span> <span data-ttu-id="707ad-107">RAW 및 AUTO 모드의 경우 XSD 생성을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="707ad-107">Use XSD generation in the case of RAW and AUTO modes.</span></span> <span data-ttu-id="707ad-108">EXPLICIT 모드의 XMLDATA 지시어의 경우에는 대체할 옵션이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="707ad-108">There is no replacement for the XMLDATA directive in EXPLICIT mode.</span></span> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="707ad-109">또한 인라인 XDR 스키마 지원에 대한 다음 정보를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="707ad-109">Also note the following about the inline XDR schema support:</span></span>  
  
-   <span data-ttu-id="707ad-110">FOR XML 쿼리 결과에 **xml** 유형의 열이 포함되어 있고 인라인 XDR 스키마를 요청하면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="707ad-110">If the FOR XML query result includes columns of **xml** type and you request an inline XDR schema, an error is returned.</span></span> <span data-ttu-id="707ad-111">인라인 XDR은 이러한 유형을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="707ad-111">Inline XDR does not support these types.</span></span>  
  
-   <span data-ttu-id="707ad-112">**(n)varchar(max)** 및 **(n)varbinary(max)** 유형은 각각 **(n)varchar(n)** 및 **varbinary(n)** 으로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="707ad-112">The **(n)varchar(max)** and **(n)varbinary(max)** types will be mapped to **(n)varchar(n)** and **varbinary(n)**, respectively.</span></span>  
  
-   <span data-ttu-id="707ad-113">호환성 모드가 90 이상으로 설정된 경우 **timestamp** 값은 **varbinary(8)** 데이터로 간주되며 이진 데이터와 같이 취급되고 다음과 같이 결과에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="707ad-113">When compatibility mode is set to 90 or higher, **timestamp** values are considered as **varbinary(8)** data, are treated like binary data, and are returned in the result as follows:</span></span>  
  
    -   <span data-ttu-id="707ad-114">**binary base64** 가 지정된 경우 Base 64 인코딩이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="707ad-114">Base 64 encoding is used when **binary base64** is specified.</span></span>  
  
    -   <span data-ttu-id="707ad-115">**binary base64** 가 지정되지 않은 경우 URL 인코딩이 AUTO 모드로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="707ad-115">URL encoding is used in AUTO mode when **binary base64** is not specified.</span></span>  
  
  
