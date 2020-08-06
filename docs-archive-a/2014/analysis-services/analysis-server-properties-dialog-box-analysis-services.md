---
title: Analysis Server 속성 대화 상자 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.SSMSIMBI.SERVERPROPERTIES.F1
- SQL12.ASVS.SQLSERVERSTUDIO.SERVERPROPERTIES.F1
helpviewer_keywords:
- Analysis Server Properties dialog box
ms.assetid: b01ec658-c191-49c9-a6cb-549b21a368ab
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6daef467782917d52fa00c6d236ce2d9305ab9e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648213"
---
# <a name="analysis-server-properties-dialog-box-analysis-services"></a><span data-ttu-id="1f97d-102">분석 서버 속성 대화 상자(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="1f97d-102">Analysis Server Properties Dialog Box (Analysis Services)</span></span>
  <span data-ttu-id="1f97d-103">**의** Analysis Server 속성 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 대화 상자를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스의 일반, 언어/데이터 정렬 및 보안 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-103">Use the **Analysis Server Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to set the general, language/collation, and security settings for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="1f97d-104">**개체 탐색기** 에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스를 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **속성** 을 선택하여 **Analysis Server 속성** 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-104">You can display the **Analysis Server Properties** dialog box by right-clicking an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance in **Object Explorer** and selecting **Properties** from the context menu.</span></span> <span data-ttu-id="1f97d-105">**Analysis Server 속성** 대화 상자에는 다음 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-105">The **Analysis Server Properties** dialog box contains the following properties.</span></span>  
  
## <a name="information-properties"></a><span data-ttu-id="1f97d-106">정보 속성</span><span class="sxs-lookup"><span data-stu-id="1f97d-106">Information Properties</span></span>  
 <span data-ttu-id="1f97d-107">이 페이지를 사용하여 서버 모드, 버전 및 호환성 수준을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-107">Use this page to view server mode, version, and compatibility level.</span></span> <span data-ttu-id="1f97d-108">각 인스턴스는 테이블 형식 또는 다차원 모델을 로드할 수 있는 기능과 함께 테이블 형식 또는 다차원 서버 모드에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-108">Each instance is installed in either Tabular or Multidimensional server mode, with the ability to load tabular or multidimensional models.</span></span> <span data-ttu-id="1f97d-109">두 모드를 모두 지원하려면 두 인스턴스를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-109">If you need to support both modes, you must install two instances.</span></span>  
  
 <span data-ttu-id="1f97d-110">**지원 되는 호환성 수준은** `DefaultCompatibilityLevel` AMO의 속성과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-110">**Supported Compatibility Level** is equivalent to the `DefaultCompatibilityLevel` property in AMO.</span></span> <span data-ttu-id="1f97d-111">설치 시 지정한 서버 배포 모드를 기반으로 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-111">It is read-only, based on the server deployment mode specified during installation.</span></span> <span data-ttu-id="1f97d-112">서버에서는 테이블 형식 서버 인스턴스에 테이블 형식 데이터베이스 백업을 복원하는 등 서버 모드 또는 버전에 따라 달라지는 작업을 수행할 때 이 속성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-112">The server checks this property when performing operations that vary by server mode or version, such as restoring a backup of a tabular database onto a tabular server instance.</span></span> <span data-ttu-id="1f97d-113">비슷한 이름 및 값을 가진 테이블 형식 또는 다차원 모델의 데이터베이스 호환성 모드와 혼동하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="1f97d-113">Do not confuse it with the database compatibility mode of tabular or multidimensional models, which have a similar names and values.</span></span> <span data-ttu-id="1f97d-114">이 서버 속성에 대한 유효한 값에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-114">Valid values for this server property include:</span></span>  
  
-   <span data-ttu-id="1f97d-115">**1100** 은 다차원 및 데이터 마이닝 모드의 경우 배포 모드 0에 대한 기본 호환성 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-115">**1100** is the default compatibility level for a deployment mode of 0, for multidimensional and data mining mode.</span></span>  
  
-   <span data-ttu-id="1f97d-116">**1103** 은 테이블 형식 모드 또는 [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)]를 지원하는 설치의 경우 배포 모드 1 또는 2에 대한 기본 호환성 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-116">**1103** is the default compatibility level for deployment modes 1 or 2, for installations supporting Tabular mode or [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)].</span></span>  
  
 <span data-ttu-id="1f97d-117">서버에서는 네임스페이스를 지원하는 클라이언트가 DISCOVER_XML_METADATA를 요청할 때 이 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-117">The server returns this value when a client supporting the namespace requests DISCOVER_XML_METADATA.</span></span> <span data-ttu-id="1f97d-118">자세한 내용은 [DISCOVER_XML_METADATA 행 집합](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1f97d-118">See [DISCOVER_XML_METADATA Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset) for more details.</span></span>  
  
## <a name="general-properties"></a><span data-ttu-id="1f97d-119">일반 속성</span><span class="sxs-lookup"><span data-stu-id="1f97d-119">General Properties</span></span>  
 <span data-ttu-id="1f97d-120">이 페이지를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 대한 폴더 위치 및 네트워크 설정과 같은 기본 및 고급 일반 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-120">Use this page to set the basic and advanced general properties, such as folder locations and network settings, for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="1f97d-121">서버 속성 페이지에는 특정 구성에 대한 서버를 튜닝하는 데 사용되는 메모리 및 스레드 풀 속성과 같이 관리자가 변경하기 쉬운 속성만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-121">The server properties page shows only those properties an administrator is more likely to change, such as memory and thread pool properties used to tune the server for certain configurations.</span></span> <span data-ttu-id="1f97d-122">다음 목록에서는 주 속성 그룹에 대한 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-122">The following list provides links to the main property groups:</span></span>  
  
-   [<span data-ttu-id="1f97d-123">일반 속성</span><span class="sxs-lookup"><span data-stu-id="1f97d-123">General Properties</span></span>](server-properties/general-properties.md)  
  
-   [<span data-ttu-id="1f97d-124">데이터 마이닝 속성</span><span class="sxs-lookup"><span data-stu-id="1f97d-124">Data Mining Properties</span></span>](server-properties/data-mining-properties.md)  
  
-   [<span data-ttu-id="1f97d-125">기능 속성</span><span class="sxs-lookup"><span data-stu-id="1f97d-125">Feature Properties</span></span>](server-properties/feature-properties.md)  
  
-   [<span data-ttu-id="1f97d-126">파일 저장소 속성</span><span class="sxs-lookup"><span data-stu-id="1f97d-126">Filestore Properties</span></span>](server-properties/filestore-properties.md)  
  
-   [<span data-ttu-id="1f97d-127">잠금 관리자 속성</span><span class="sxs-lookup"><span data-stu-id="1f97d-127">Lock Manager Properties</span></span>](server-properties/lock-manager-properties.md)  
  
-   [<span data-ttu-id="1f97d-128">로그 속성</span><span class="sxs-lookup"><span data-stu-id="1f97d-128">Log Properties</span></span>](server-properties/log-properties.md)  
  
-   [<span data-ttu-id="1f97d-129">메모리 속성</span><span class="sxs-lookup"><span data-stu-id="1f97d-129">Memory Properties</span></span>](server-properties/memory-properties.md)  
  
-   [<span data-ttu-id="1f97d-130">네트워크 속성</span><span class="sxs-lookup"><span data-stu-id="1f97d-130">Network Properties</span></span>](server-properties/network-properties.md)  
  
-   [<span data-ttu-id="1f97d-131">OLAP 속성</span><span class="sxs-lookup"><span data-stu-id="1f97d-131">OLAP Properties</span></span>](server-properties/olap-properties.md)  
  
-   [<span data-ttu-id="1f97d-132">보안 속성</span><span class="sxs-lookup"><span data-stu-id="1f97d-132">Security Properties</span></span>](server-properties/security-properties.md)  
  
-   [<span data-ttu-id="1f97d-133">스레드 풀 속성</span><span class="sxs-lookup"><span data-stu-id="1f97d-133">Thread Pool Properties</span></span>](server-properties/thread-pool-properties.md)  
  
## <a name="language-collation-properties"></a><span data-ttu-id="1f97d-134">언어/데이터 정렬 속성</span><span class="sxs-lookup"><span data-stu-id="1f97d-134">Language Collation Properties</span></span>  
 <span data-ttu-id="1f97d-135">이 페이지를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]의 기본 언어 및 데이터 정렬 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-135">Use this page to set the default language and collation options for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="1f97d-136">다음 목록에는 각 옵션에 대한 간략한 설명이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-136">The following list contains short descriptions of each option.</span></span> <span data-ttu-id="1f97d-137">자세한 내용은 [Languages and Collations &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1f97d-137">See [Languages and Collations &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md) for more detailed descriptions.</span></span>  
  
-   <span data-ttu-id="1f97d-138">**이진** 은 각 문자에 대해 정의된 비트 패턴을 기준으로 데이터를 정렬 및 비교하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-138">**Binary** is used to sort and compare data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="1f97d-139">이진 정렬 순서는 대/소문자(소문자가 대문자 앞에 와야 함) 및 악센트를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-139">Binary sort order is case-sensitive, that is, lowercase precedes uppercase, and accent-sensitive.</span></span> <span data-ttu-id="1f97d-140">이것은 가장 빠른 정렬 순서입니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-140">This is the fastest sorting order.</span></span>  
  
     <span data-ttu-id="1f97d-141">이 옵션을 선택하지 않으면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 관련된 언어 또는 알파벳에 대해 사전에 정의된 정렬 및 비교 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-141">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] follows sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1f97d-142">이 옵션을 선택하면 **대/소문자 구분**, **악센트 구분**, **일본어 가나 구분**및 **전자/반자 구분** 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-142">If this option is selected, the **Case-Sensitive**, **Accent-Sensitive**, **Kana-Sensitive**, and **Width-Sensitive** options are disabled.</span></span>  
  
-   <span data-ttu-id="1f97d-143">**이진 2** 는 각 문자에 대해 정의된 비트 패턴을 기준으로 유니코드 데이터를 정렬 및 비교하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-143">**Binary 2** is used to sort and compare Unicode data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="1f97d-144">이진 정렬 순서는 대/소문자(소문자가 대문자 앞에 와야 함) 및 악센트를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-144">Binary sort order is case-sensitive, that is, lowercase precedes uppercase, and accent-sensitive.</span></span> <span data-ttu-id="1f97d-145">이것은 가장 빠른 정렬 순서입니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-145">This is the fastest sorting order.</span></span>  
  
-   <span data-ttu-id="1f97d-146">**대/소문자 구분** 은 관련된 언어 또는 알파벳에 대해 제공된 사전 규칙을 기준으로 데이터를 정렬 및 비교하고 대문자와 소문자를 구분하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-146">**Case-Sensitive** is used to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between uppercase and lowercase letters.</span></span>  
  
     <span data-ttu-id="1f97d-147">이 옵션을 선택하지 않으면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 대문자와 소문자가 동일한 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-147">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the uppercase and lowercase versions of letters to be equal.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="1f97d-148">는 **대/소문자 구분** 을 선택 하지 않은 경우 대문자와 관련 하 여 소문자 정렬 순서를 정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-148">does not define whether lowercase letters sort lower or higher in relation to uppercase letters when **Case-sensitive** is not selected.</span></span>  
  
-   <span data-ttu-id="1f97d-149">**악센트 구분** 은 관련된 언어 또는 알파벳에 대해 제공된 사전 규칙을 기준으로 데이터를 정렬 및 비교하고 악센트가 있는 문자와 악센트가 없는 문자를 구분하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-149">**Accent-Sensitive** is used to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between accented and unaccented characters.</span></span> <span data-ttu-id="1f97d-150">예를 들어 'a'와 'á'는 같지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-150">For example, 'a' is not equal to 'á'.</span></span>  
  
     <span data-ttu-id="1f97d-151">이 옵션을 선택하지 않으면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 악센트가 있는 문자와 악센트가 없는 문자가 동일한 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-151">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the accented and unaccented versions of letters to be equal.</span></span>  
  
-   <span data-ttu-id="1f97d-152">**일본어 가나 구분** 은 관련된 언어 또는 알파벳에 대해 제공된 사전 규칙을 기준으로 데이터를 정렬 및 비교하고 히라가나와 가타카나 등 두 가지 유형의 일본어 가나 문자를 구분하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-152">**Kana-Sensitive** is used to and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between the two types of Japanese kana characters: Hiragana and Katakana.</span></span>  
  
     <span data-ttu-id="1f97d-153">이 옵션을 선택하지 않으면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 히라가나 문자와 가타카나 문자가 동일한 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-153">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers Hiragana and Katakana characters to be equal.</span></span>  
  
-   <span data-ttu-id="1f97d-154">**전자/반자 구분** 은 관련된 언어 또는 알파벳에 대해 제공된 사전 규칙을 기준으로 데이터를 정렬 및 비교하고 단일 바이트 문자(반자)와 더블바이트 문자로 표시될 때의 동일한 문자(전자)를 구분하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-154">**Width-Sensitive** is used to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between a single-byte character (half-width) and the same character when represented as a double-byte character (full-width).</span></span>  
  
     <span data-ttu-id="1f97d-155">이 옵션을 선택하지 않으면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 싱글바이트와 더블바이트로 표시된 같은 문자를 동일한 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-155">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the single-byte and double-byte representation of the same character to be equal.</span></span>  
  
## <a name="security-properties"></a><span data-ttu-id="1f97d-156">보안 속성</span><span class="sxs-lookup"><span data-stu-id="1f97d-156">Security Properties</span></span>  
 <span data-ttu-id="1f97d-157">이 페이지를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스의 서버 관리자 역할에 속하는 Windows 사용자 및 그룹 계정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-157">Use this page to specify the Windows user and group accounts belonging to the server administrator role for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="1f97d-158">이 역할의 멤버 자격에 대한 권한이 있으면 데이터베이스를 만들거나 처리하고 서버 속성을 수정하고 이 역할의 다른 멤버를 추가 또는 제거하거나 추적을 시작하는 등 서버 차원 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f97d-158">Membership in this role conveys permission to perform server-wide tasks, such as creating or processing a database, modifying server properties, adding or removing other members of this role, or launching a trace.</span></span> <span data-ttu-id="1f97d-159">자세한 내용은 [서버 관리자 권한 부여 &#40;Analysis Services&#41;](instances/grant-server-admin-rights-to-an-analysis-services-instance.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f97d-159">See [Grant Server Administrator Permissions &#40;Analysis Services&#41;](instances/grant-server-admin-rights-to-an-analysis-services-instance.md) for details.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f97d-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1f97d-160">See Also</span></span>  
 <span data-ttu-id="1f97d-161">[Analysis Services 인스턴스의 서버 모드 확인](instances/determine-the-server-mode-of-an-analysis-services-instance.md) </span><span class="sxs-lookup"><span data-stu-id="1f97d-161">[Determine the Server Mode of an Analysis Services Instance](instances/determine-the-server-mode-of-an-analysis-services-instance.md) </span></span>  
 <span data-ttu-id="1f97d-162">[Analysis Services에서 서버 속성 구성](server-properties/server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="1f97d-162">[Configure Server Properties in Analysis Services](server-properties/server-properties-in-analysis-services.md) </span></span>  
 <span data-ttu-id="1f97d-163">[Analysis Services에서 지 원하는 인증 방법](instances/authentication-methodologies-supported-by-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="1f97d-163">[Authentication methodologies supported by Analysis Services](instances/authentication-methodologies-supported-by-analysis-services.md) </span></span>  
 <span data-ttu-id="1f97d-164">[역할 및 사용 권한 &#40;Analysis Services&#41;](multidimensional-models/roles-and-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="1f97d-164">[Roles and Permissions &#40;Analysis Services&#41;](multidimensional-models/roles-and-permissions-analysis-services.md) </span></span>  
 [<span data-ttu-id="1f97d-165">언어 및 데이터 정렬&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1f97d-165">Languages and Collations &#40;Analysis Services&#41;</span></span>](languages-and-collations-analysis-services.md)  
  
  
