---
title: 주석이 추가 된 XDR 스키마를 해당 XSD 스키마로 변환 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XDR schemas, converting schemas
- annotated XSD schemas, converting schemas
- XDR to XSD Converter tool [SQLXML]
- XDR schemas [SQLXML], converting
- converting annotated schemas
- mapping schema [SQLXML], conversions
- XSD schemas [SQLXML], converting schemas
ms.assetid: 151c94a8-66d3-4c46-a5ff-a22df456940a
author: rothja
ms.author: jroth
ms.openlocfilehash: c36eb17aacb61a47fad0f389de9a3c216202827d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652724"
---
# <a name="converting-annotated-xdr-schemas-to-equivalent-xsd-schemas-sqlxml-40"></a><span data-ttu-id="6a54e-102">주석이 추가된 XDR 스키마를 해당 XSD 스키마로 변환(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="6a54e-102">Converting Annotated XDR Schemas to Equivalent XSD Schemas (SQLXML 4.0)</span></span>
  <span data-ttu-id="6a54e-103">XSD(XML 스키마 정의) 언어는 XDR(XML-Data Reduced) 스키마 정의 언어의 후속 제품입니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-103">The XML Schema Definition (XSD) language is the successor to the XML-Data Reduced (XDR) schema definition language.</span></span> <span data-ttu-id="6a54e-104">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0에서는 새로 XSD를 지원하므로 XSD를 사용하여 주석이 추가된 새 스키마를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-104">With the introduction of XSD support in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, it is assumed that new annotated schemas are created using XSD.</span></span> <span data-ttu-id="6a54e-105">SQLXML 4.0에는 기존의 주석이 추가된 XDR 스키마를 해당하는 XSD 스키마로 변환하는 데 도움을 주기 위한 XDR-XSD 변환기 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-105">SQLXML 4.0 includes an XDR to XSD converter tool that is designed to help you convert your existing annotated XDR schemas to equivalent XSD schemas.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6a54e-106">주석이 추가된 스키마를 SQLXML 4.0에서 사용하기 위해 XSD로 변환하려는 경우에만 이 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-106">Use this tool only when you want to convert annotated XDR schemas to XSD for use with SQLXML 4.0.</span></span> <span data-ttu-id="6a54e-107">이 도구는 범용 XDR-XSD 변환 도구가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-107">This is not a general purpose XDR to XSD converter tool.</span></span> <span data-ttu-id="6a54e-108">따라서 변환된 XSD 스키마를 다른 환경에서 사용할 경우 원래 XDR 스키마와 동일하게 동작하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-108">The converted XSD schemas may not behave the same as the original XDR schemas when used in other environments.</span></span>  
  
 <span data-ttu-id="6a54e-109">입력 XDR 파일에서 XML 선언 내에 인코딩을 지정하는 경우 이것이 생성되는 XSD 출력 파일의 인코딩이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-109">If the input XDR file specifies the encoding within the XML declaration, this becomes the encoding of the XSD output file that is generated.</span></span>  
  
 <span data-ttu-id="6a54e-110">변환기 도구(Cvtschema.exe)는 Program Files\SQLXML 4.0\bin 폴더에 설치되며 명령 프롬프트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-110">The converter tool (Cvtschema.exe) is installed in the Program Files\SQLXML 4.0\bin folder and is executed at the command prompt.</span></span>  
  
 <span data-ttu-id="6a54e-111">일반 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-111">This is the general syntax:</span></span>  
  
```  
cvtschema XDRFileName, [-y], [-w] [-?]  
```  
  
 <span data-ttu-id="6a54e-112">위치:</span><span class="sxs-lookup"><span data-stu-id="6a54e-112">Where:</span></span>  
  
 <span data-ttu-id="6a54e-113">XDRFileName</span><span class="sxs-lookup"><span data-stu-id="6a54e-113">XDRFileName</span></span>  
 <span data-ttu-id="6a54e-114">XSD로 변환될 XDR 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-114">Is the name of the XDR file that is to be converted to XSD.</span></span> <span data-ttu-id="6a54e-115">이 도구는 입력 XDR 파일을 읽어 들이고 현재 디렉터리에 XSD 출력 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-115">The tool reads the input XDR file and creates an XSD output file in the current working directory.</span></span> <span data-ttu-id="6a54e-116">입력 파일의 확장명이 .xdr 또는 .xml인 경우 생성되는 출력 XDR 파일은 이름은 같지만 확장명은 .xsd입니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-116">If the input file has an .xdr or .xml extension, the output XSD file is created with the same name but with an .xsd extension.</span></span> <span data-ttu-id="6a54e-117">입력 파일의 확장명이 .xml 또는 .xdr이 아니거나 확장명이 없는 경우 출력 파일이 같은 이름으로 생성되고 입력 파일 이름에 .xsd 확장명이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-117">If the input file extension is other than .xml or .xdr (or if the extension is missing), the output file is created with the same name and the .xsd extension is appended to the input file name.</span></span> <span data-ttu-id="6a54e-118">예를 들어 입력 XDR 파일 이름이 SampleFile.abc인 경우 결과 XSD는 SampleFile.abc.xsd로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-118">For example, if the input XDR file name is SampleFile.abc, the resulting XSD is saved as SampleFile.abc.xsd.</span></span>  
  
 <span data-ttu-id="6a54e-119">-y</span><span class="sxs-lookup"><span data-stu-id="6a54e-119">-y</span></span>  
 <span data-ttu-id="6a54e-120">(옵션) 기존 XSD 파일을 변환기 도구에서 생성되는 XSD 파일로 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-120">(Optional) Overwrites the existing XSD file with the XSD file that is generated by the converter tool.</span></span> <span data-ttu-id="6a54e-121">이 플래그를 지정하지 않으면 도구에서는 기존 XSD 파일을 덮어쓸지 여부를 지정하라는 메시지를 표시하고 출력 파일 이름을 변경할 수 있는 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-121">If the flag is not specified, the tool prompts you to specify whether you want to overwrite the existing XSD file and gives you the option to change the output file name.</span></span>  
  
 <span data-ttu-id="6a54e-122">-w</span><span class="sxs-lookup"><span data-stu-id="6a54e-122">-w</span></span>  
 <span data-ttu-id="6a54e-123">(옵션) 도구의 변환 프로세스에서 생성된 심각하지 않은 경고를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-123">(Optional) Returns nonfatal warnings that are generated in the conversion process by the tool.</span></span> <span data-ttu-id="6a54e-124">기본적으로 심각한 오류에 대한 메시지만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-124">By default, the tool displays messages only for fatal errors.</span></span>  
  
 <span data-ttu-id="6a54e-125">-?</span><span class="sxs-lookup"><span data-stu-id="6a54e-125">-?</span></span>  
 <span data-ttu-id="6a54e-126">`cvtschema`에서 지정할 수 있는 옵션 목록을 설명과 함께 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6a54e-126">Returns a list of options that you can specify with `cvtschema`, along with an explanation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a54e-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a54e-127">See Also</span></span>  
 <span data-ttu-id="6a54e-128">[&#40;SQLXML 4.0&#41;XSD 데이터 형식을 XPath 데이터 형식에 매핑](../../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="6a54e-128">[Mapping XSD Data Types to XPath Data Types &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="6a54e-129">&#40;SQLXML 4.0&#41;XSD 주석</span><span class="sxs-lookup"><span data-stu-id="6a54e-129">XSD Annotations &#40;SQLXML 4.0&#41;</span></span>](../../sqlxml-annotated-xsd-schemas-using/xsd-annotations-sqlxml-4-0.md)  
  
  
