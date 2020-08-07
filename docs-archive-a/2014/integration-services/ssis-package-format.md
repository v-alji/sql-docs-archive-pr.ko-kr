---
title: SSIS 패키지 형식 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cfe0e5dc-5be3-4222-b721-fe83665edd94
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 524c65ac5682b8efe8c4191697eb540f9acca82b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731880"
---
# <a name="ssis-package-format"></a><span data-ttu-id="a6f3b-102">SSIS 패키지 형식</span><span class="sxs-lookup"><span data-stu-id="a6f3b-102">SSIS Package Format</span></span>
  <span data-ttu-id="a6f3b-103">현재 버전의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]에서는 보다 쉽게 형식을 읽고 패키지를 비교할 수 있도록 패키지 형식(.dtsx 파일)이 크게 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-103">In the current release of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], significant changes were made to the package format (.dtsx file) to make it easier to read the format and to compare packages.</span></span> <span data-ttu-id="a6f3b-104">또한 이진 형식으로 저장 된 충돌 하는 변경 내용 또는 변경 내용이 포함 되지 않은 패키지를 더욱 안정적으로 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-104">You can also more reliably merge packages that don't contain conflicting changes or changes stored in binary format.</span></span>  
  
 <span data-ttu-id="a6f3b-105">현재 PACKAGE.DTSX 패키지 파일 형식을 보려면 [ \[ Package.dtsx \] : 데이터 변환 서비스 패키지 XML 파일 형식 사양](https://go.microsoft.com/fwlink/?LinkId=233251)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-105">To view the current DTSX package file format, see [\[MS-DTSX\]: Data Transformation Services Package XML File Format Specification](https://go.microsoft.com/fwlink/?LinkId=233251).</span></span>  
  
 <span data-ttu-id="a6f3b-106">다음 목록에서는 파일 형식 변경 내용을 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-106">The following list outlines the file format changes.</span></span> <span data-ttu-id="a6f3b-107">이러한 변경 내용의 코드 예제를 보려면 [SQL Server 2012의 패키지 형식 변경 내용](https://go.microsoft.com/fwlink/?LinkId=233255)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-107">To view code examples of these changes, see [Package Format Changes in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=233255).</span></span>  
  
-   <span data-ttu-id="a6f3b-108">보다 쉽게 .dtsx 파일을 읽고 이해하도록 서식 변환이 적용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-108">Formatting conventions have been applied to make it easier to read and understand the .dtsx file.</span></span>  
  
-   <span data-ttu-id="a6f3b-109">형식이 더욱 간결해졌습니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-109">The format is more concise.</span></span> <span data-ttu-id="a6f3b-110">PackageFormatVersion을 제외하고 각 속성의 개별 요소가 특성으로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-110">Separate elements for each property have been persisted as attributes, with the exception of the PackageFormatVersion.</span></span> <span data-ttu-id="a6f3b-111">특성이 사전순으로 나열되며, 기본값을 가진 속성이 더 이상 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-111">Attributes are listed alphabetically, and properties that have default values are no longer persisted.</span></span> <span data-ttu-id="a6f3b-112">마지막으로, 여러 번 나타날 수 있는 요소가 이제 부모 요소 내에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-112">Finally, elements that can appear multiple times, are now contained within a parent element.</span></span>  
  
-   <span data-ttu-id="a6f3b-113">다른 개체에서 참조할 수 있는 패키지 내의 개체가 대부분 패키지 XML에 정의된 `refId` 특성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-113">Most objects within a package that can be referred to by other objects now have a `refId` attribute defined in the package XML.</span></span> <span data-ttu-id="a6f3b-114">지속적인 계보 ID 대신 이제 `refID`가 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-114">Instead of persisting lineage IDs, the `refID` is now persisted.</span></span> <span data-ttu-id="a6f3b-115">계보 ID는 런타임 내에서 계속 사용되며 패키지가 로드될 때 다시 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-115">Lineage IDs are still used within the runtime and regenerated when the package is loaded.</span></span>  
  
     <span data-ttu-id="a6f3b-116">`refId` 값은 읽고 이해할 수 있는 고유 문자열로서, GUID 또는 정수 값과 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-116">The `refId` value is a unique string that is readable and understandable, compared to GUIDs or integer values.</span></span> <span data-ttu-id="a6f3b-117">문자열은 이전 버전의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]에서 패키지 구성에 사용되는 경로 값과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-117">The string is similar to path values used for package configurations in previous releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="a6f3b-118">두 가지 패키지 버전 간의 변경 내용을 병합할 경우 찾기/바꾸기 작업에서 `refId`를 사용하여 해당 개체에 대한 모든 참조를 올바르게 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-118">If you are merging changes between two versions of a package, the `refId` can be used in find/replace operations to ensure that all references to that object have been correctly updated.</span></span>  
  
-   <span data-ttu-id="a6f3b-119">레이아웃 정보가 CData 섹션에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-119">The layout information is contained in a CData section.</span></span>  
  
-   <span data-ttu-id="a6f3b-120">주석은 일반 텍스트로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-120">Annotations are persisted in cleartext.</span></span> <span data-ttu-id="a6f3b-121">따라서 설명서 자동 생성에 대한 정보를 보다 쉽게 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-121">This makes it easier to extract the information for automated generation of documentation.</span></span>  
  
  
