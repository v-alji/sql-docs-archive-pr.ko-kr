---
title: 큐브 번역 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- multiple language support [Analysis Services]
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- cubes [Analysis Services], translations
- OLAP objects [Analysis Services], translations
- translations [Analysis Services], cubes
ms.assetid: 4e4fd6a4-d324-4508-b75a-2a57de9ab8ff
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8cd4347baae8504ef5dd0f13a3adcca634c49ea2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651936"
---
# <a name="cube-translations"></a><span data-ttu-id="7b27b-102">큐브 번역</span><span class="sxs-lookup"><span data-stu-id="7b27b-102">Cube Translations</span></span>
  <span data-ttu-id="7b27b-103">번역은 표시된 레이블과 캡션을 한 언어에서 다른 언어로 변경하는 간단한 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-103">A translation is a simple mechanism to change the displayed labels and captions from one language to another.</span></span> <span data-ttu-id="7b27b-104">각 번역은 한 쌍의 값인 번역된 텍스트가 있는 문자열과 언어 ID가 있는 번호로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-104">Each translation is defined as a pair of values: a string with the translated text, and a number with the language ID.</span></span> <span data-ttu-id="7b27b-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 있는 모든 개체를 번역할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="7b27b-105">Translations are available for all objects in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="7b27b-106">차원의 특성 값도 번역할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-106">Dimensions can also have the attribute values translated.</span></span> <span data-ttu-id="7b27b-107">클라이언트 애플리케이션에서는 사용자가 정의한 언어 설정과 이 언어로 모든 캡션 및 레이블을 표시하는 스위치를 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-107">The client application is responsible for finding the language setting that the user has defined, and switch to display all captions and labels to that language.</span></span> <span data-ttu-id="7b27b-108">개체는 원하는 만큼 다양하게 번역할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-108">An object can have as many translations as you want.</span></span>  
  
 <span data-ttu-id="7b27b-109">단순 <xref:Microsoft.AnalysisServices.Translation> 개체는 언어 ID 번호와 번역된 캡션으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-109">A simple <xref:Microsoft.AnalysisServices.Translation> object is composed of: language ID number, and translated caption.</span></span> <span data-ttu-id="7b27b-110">언어 ID 번호는 언어 ID가 있는 `Integer`이고</span><span class="sxs-lookup"><span data-stu-id="7b27b-110">The language ID number is an `Integer` with the language ID.</span></span> <span data-ttu-id="7b27b-111">번역된 캡션은 번역된 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-111">The translated caption is the translated text.</span></span>  
  
 <span data-ttu-id="7b27b-112">에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 큐브 번역은 캡션 또는 표시 폴더와 같은 큐브 개체의 이름을 언어별로 표현한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-112">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], a cube translation is a language-specific representation of the name of a cube object, such as a caption or a display folder.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="7b27b-113">에서는 차원 및 멤버 이름의 번역도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-113">also supports translations of dimension and member names.</span></span>  
  
 <span data-ttu-id="7b27b-114">번역은 여러 언어를 지원할 수 있는 클라이언트 애플리케이션에 대한 서버 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-114">Translations provide server support for client applications that can support multiple languages.</span></span> <span data-ttu-id="7b27b-115">여러 나라의 사용자가 큐브 데이터를 보는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-115">Frequently, users from different countries view cube data.</span></span> <span data-ttu-id="7b27b-116">이러한 사용자가 큐브의 메타데이터를 보고 이해할 수 있도록 큐브의 여러 요소를 다른 언어로 번역할 수 있으면 매우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-116">It is useful to be able to translate various elements of a cube into a different language so that these users can view and understand the cube's metadata.</span></span> <span data-ttu-id="7b27b-117">예를 들어 프랑스에 있는 비즈니스 사용자는 프랑스어 로캘이 설정된 워크스테이션에서 큐브에 액세스하여 프랑스어로 개체 속성 값을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-117">For example, a business user in France can access a cube from a workstation with a French locale setting, and view the object property values in French.</span></span> <span data-ttu-id="7b27b-118">마찬가지로 독일에 있는 비즈니스 사용자는 독일어 로캘이 설정된 워크스테이션에서 동일한 큐브에 액세스하여 독일어로 동일한 개체 속성 값을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-118">Similarly, a business user in Germany can access the same cube from a workstation with a German locale setting and view the object property values in German.</span></span>  
  
 <span data-ttu-id="7b27b-119">클라이언트 컴퓨터의 데이터 정렬 및 언어 정보는 LCID(로캘 ID) 형식으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-119">The collation and language information for the client computer is stored in the form of a locale identifier (LCID).</span></span> <span data-ttu-id="7b27b-120">연결 시 클라이언트는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 LCID를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-120">Upon connection, the client passes the LCID to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="7b27b-121">인스턴스는 LCID를 기준으로 각 비즈니스 사용자에게 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체에 대한 메타데이터를 제공할 때 사용할 번역을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-121">The instance uses the LCID to determine which set of translations to use when providing metadata for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects to each business user.</span></span> <span data-ttu-id="7b27b-122">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체에 지정된 번역이 없으면 콘텐츠가 기본 언어로 클라이언트에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b27b-122">If an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object does not contain the specified translation, the default language is used to return the content back to the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b27b-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7b27b-123">See Also</span></span>  
 <span data-ttu-id="7b27b-124">[차원 번역](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md) </span><span class="sxs-lookup"><span data-stu-id="7b27b-124">[Dimension Translations](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md) </span></span>  
 <span data-ttu-id="7b27b-125">[번역 &#40;Analysis Services&#41;](../translations-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="7b27b-125">[Translations &#40;Analysis Services&#41;](../translations-analysis-services.md) </span></span>  
 [<span data-ttu-id="7b27b-126">세계화 팁과 모범 사례&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7b27b-126">Globalization Tips and Best Practices &#40;Analysis Services&#41;</span></span>](../globalization-tips-and-best-practices-analysis-services.md)  
  
  
