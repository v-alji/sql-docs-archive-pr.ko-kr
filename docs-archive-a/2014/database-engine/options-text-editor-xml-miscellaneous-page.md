---
title: 옵션 (텍스트 편집기-XML-기타 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 1a9509f0-c663-4b31-b396-7f5dc4371651
author: rothja
ms.author: jroth
ms.openlocfilehash: d937368d30122442ccbc40372a6b8e1cabc141e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727328"
---
# <a name="options-text-editor---xml---miscellaneous-page"></a><span data-ttu-id="6b629-102">옵션(텍스트 편집기 - XML - 기타 페이지)</span><span class="sxs-lookup"><span data-stu-id="6b629-102">Options (Text Editor - XML - Miscellaneous Page)</span></span>

<span data-ttu-id="6b629-103">**옵션** 대화 상자를 사용하여 XML 편집기의 자동 완성 및 스키마 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-103">The **Options** dialog box lets you change the autocompletion and schema settings for the XML Editor.</span></span> <span data-ttu-id="6b629-104">이러한 설정은 **도구** 메뉴에서 **옵션**을 클릭하고 **텍스트 편집기** 폴더를 확장한 다음 **XML** 과 **기타** 를 차례로 클릭하면 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-104">These settings are available when, on the **Tools** menu, you click **Options**, expand the **Text Editor** folder, click **XML** and then click **Miscellaneous** .</span></span>  
  
## <a name="auto-insert"></a><span data-ttu-id="6b629-105">자동 삽입</span><span class="sxs-lookup"><span data-stu-id="6b629-105">Auto Insert</span></span>  
 <span data-ttu-id="6b629-106">**닫기 태그**</span><span class="sxs-lookup"><span data-stu-id="6b629-106">**Close tags**</span></span>  
 <span data-ttu-id="6b629-107">XML 요소를 만들 때 텍스트 편집기가 닫는 태그를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-107">The Text Editor adds close tags when authoring XML elements.</span></span> <span data-ttu-id="6b629-108">요소 시작 태그를 선택하면 일치하는 네임스페이스 접두사와 함께 일치하는 닫는 태그가 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-108">If an element start tag is selected, the editor inserts the matching close tag, including a matching namespace prefix.</span></span> <span data-ttu-id="6b629-109">이 확인란은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-109">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="6b629-110">**특성 따옴표**</span><span class="sxs-lookup"><span data-stu-id="6b629-110">**Attribute quotes**</span></span>  
 <span data-ttu-id="6b629-111">XML 특성을 작성할 때 편집기에서 `="``"` 문자를 삽입하고 따옴표 안에 캐럿(**^** )을 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-111">When authoring XML attributes, the editor inserts the `="``"` characters and positions the caret (**^)** inside the quotation marks.</span></span> <span data-ttu-id="6b629-112">이 확인란은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-112">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="6b629-113">**네임스페이스 선언**</span><span class="sxs-lookup"><span data-stu-id="6b629-113">**Namespace declarations**</span></span>  
 <span data-ttu-id="6b629-114">필요할 때마다 네임스페이스 선언이 자동으로 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-114">The editor automatically inserts namespace declarations wherever they are needed.</span></span> <span data-ttu-id="6b629-115">이 확인란은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-115">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="6b629-116">**기타 태그(주석, CDATA)**</span><span class="sxs-lookup"><span data-stu-id="6b629-116">**Other markup (Comments, CDATA)**</span></span>  
 <span data-ttu-id="6b629-117">주석, CDATA, DOCTYPE, 처리 명령 및 기타 태그가 자동 완성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-117">Comments, CDATA, DOCTYPE, processing instructions, and other markup is autocompleted.</span></span> <span data-ttu-id="6b629-118">이 확인란은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-118">This check box is selected by default.</span></span>  
  
## <a name="network"></a><span data-ttu-id="6b629-119">네트워크</span><span class="sxs-lookup"><span data-stu-id="6b629-119">Network</span></span>  
 <span data-ttu-id="6b629-120">**DTD 및 스키마 자동 다운로드**</span><span class="sxs-lookup"><span data-stu-id="6b629-120">**Automatically download DTDs and schemas**</span></span>  
 <span data-ttu-id="6b629-121">스키마와 DTD(문서 유형 정의)를 HTTP 위치에서 자동으로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-121">Schemas and document type definitions (DTDs) are automatically downloaded from HTTP locations.</span></span> <span data-ttu-id="6b629-122">자동 프록시 서버 검색을 사용하는 경우 이 기능은 System.Net을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-122">This feature uses System.Net with autoproxy server detection enabled.</span></span> <span data-ttu-id="6b629-123">이 확인란은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-123">This check box is selected by default.</span></span>  
  
## <a name="outlining"></a><span data-ttu-id="6b629-124">개요</span><span class="sxs-lookup"><span data-stu-id="6b629-124">Outlining</span></span>  
 <span data-ttu-id="6b629-125">**개요 모드로 파일 열기**</span><span class="sxs-lookup"><span data-stu-id="6b629-125">**Enter outlining mode when files open**</span></span>  
 <span data-ttu-id="6b629-126">파일을 열 때 개요 기능을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-126">Turns on the outlining feature when a file is opened.</span></span> <span data-ttu-id="6b629-127">이 확인란은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-127">This check box is selected by default.</span></span>  
  
## <a name="caching"></a><span data-ttu-id="6b629-128">캐싱</span><span class="sxs-lookup"><span data-stu-id="6b629-128">Caching</span></span>  
 <span data-ttu-id="6b629-129">**스키마**</span><span class="sxs-lookup"><span data-stu-id="6b629-129">**Schemas**</span></span>  
 <span data-ttu-id="6b629-130">스키마 캐시의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-130">Specifies the location of the schema cache.</span></span> <span data-ttu-id="6b629-131">찾아보기 단추(...)를 클릭하면 현재 스키마 캐시 위치가 새 창에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6b629-131">The Browse button (...) opens the current schema cache location in a new window.</span></span> <span data-ttu-id="6b629-132">기본 위치는 *\<Management Studio install directory>* \Xml\schemas..</span><span class="sxs-lookup"><span data-stu-id="6b629-132">The default location is *\<Management Studio install directory>* \Xml\Schemas.</span></span>  
