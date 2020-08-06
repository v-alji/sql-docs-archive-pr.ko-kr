---
title: 개인 설정을 통해 OLAP 확장 Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
author: minewiskan
ms.author: owend
ms.openlocfilehash: 93669980e989b1cb11673f45c111de3609bbe920
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741395"
---
# <a name="extending-olap-through-personalizations"></a><span data-ttu-id="7d642-102">개별화를 통해 OLAP 확장</span><span class="sxs-lookup"><span data-stu-id="7d642-102">Extending OLAP through personalizations</span></span>
  <span data-ttu-id="7d642-103">Microsoft [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)]에서는 MDX(Multidimensional Expressions) 및 DMX(Data Mining Extension) 언어와 함께 사용할 수 있는 다양한 내장 함수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7d642-103">Microsoft  [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] supplies many intrinsic functions for use with the Multidimensional Expressions (MDX) and Data Mining Extensions (DMX) languages.</span></span> <span data-ttu-id="7d642-104">이러한 함수를 사용하여 표준 통계 계산을 비롯하여 계층에서의 멤버 이동에 이르는 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d642-104">These functions are designed to accomplish everything from standard statistical calculations to traversing members in a hierarchy.</span></span> <span data-ttu-id="7d642-105">그러나 복잡하고 강력한 다른 제품에서도 그렇듯이 제품의 기능을 더 확장할 필요성은 언제나 있기 마련입니다.</span><span class="sxs-lookup"><span data-stu-id="7d642-105">However, as with any other complex and robust product, there is always the need to extend the functionality of such a product further.</span></span>  
  
 <span data-ttu-id="7d642-106">따라서 표준 기능이 충분하지 않을 때마다 업무 요구 사항을 완전히 충족시키기 위해 Analysis Services에서는 서비스 인스턴스에 어셈블리 및 개인 설정 확장 프로그램을 추가하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7d642-106">Therefore, Analysis Services provides you with the ability to add assemblies and personalized extensions to an instance of the service, in order to complete your business needs whenever the standard functionality is not enough.</span></span>  
  
## <a name="assemblies"></a><span data-ttu-id="7d642-107">어셈블리</span><span class="sxs-lookup"><span data-stu-id="7d642-107">Assemblies</span></span>  
 <span data-ttu-id="7d642-108">어셈블리를 사용하면 MDX와 DMX의 비즈니스 기능을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d642-108">Assemblies enable you to extend the business functionality of MDX and DMX.</span></span> <span data-ttu-id="7d642-109">원하는 기능을 작성하여 DLL(동적 연결 라이브러리)과 같은 라이브러리에 추가한 후 이 라이브러리를 Analysis Services 인스턴스 또는 Analysis Services 데이터베이스에 어셈블리로 추가하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d642-109">You build the functionality that you want into a library, such as a dynamic link library (DLL), then add the library as an assembly to an instance of Analysis Services or to an Analysis Services database.</span></span> <span data-ttu-id="7d642-110">그런 다음 MDX 및 DMX 식, 프로시저, 계산, 동작 및 클라이언트 애플리케이션에서 라이브러리의 공용 메서드를 사용자 정의 함수로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d642-110">The public methods in the library are then exposed as user-defined functions to MDX and DMX expressions, procedures, calculations, actions, and client applications.</span></span>  
  
## <a name="personalized-extensions"></a><span data-ttu-id="7d642-111">개인 설정 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="7d642-111">Personalized Extensions</span></span>  
 <span data-ttu-id="7d642-112">SQL Server Analysis Services 개인 설정 확장 프로그램은 플러그 인 아키텍처 구현 개념의 토대입니다.</span><span class="sxs-lookup"><span data-stu-id="7d642-112">SQL Server Analysis Services personalization extensions are the foundation of the idea of implementing a plug-in architecture.</span></span> <span data-ttu-id="7d642-113">Analysis Services 개인 설정 확장 프로그램은 기존 관리 어셈블리 아키텍처를 간단 하 고 세련 되 게 수정 하 고 Analysis Services [Microsoft.analysisservices.sharepoint.integration.dll AdomdServer](/previous-versions/sql/sql-server-2014/ms131779(v=sql.120)) 개체 모델, MDX (Multidimensional Expressions) 구문 및 스키마 행 집합 전체에 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d642-113">Analysis Services personalization extensions are a simple and elegant modification to the existing managed assembly architecture and are exposed throughout the Analysis Services [Microsoft.AnalysisServices.AdomdServer](/previous-versions/sql/sql-server-2014/ms131779(v=sql.120)) object model, Multidimensional Expressions (MDX) syntax, and schema rowsets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d642-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7d642-114">See Also</span></span>  
 <span data-ttu-id="7d642-115">[다차원 모델 어셈블리 관리](../multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="7d642-115">[Multidimensional Model Assemblies Management](../multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="7d642-116">Analysis Services 개인 설정 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="7d642-116">Analysis Services Personalization Extensions</span></span>](analysis-services-personalization-extensions.md)  
  
  
