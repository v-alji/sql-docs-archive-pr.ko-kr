---
title: OLAP 기능 확장 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 49a17ff3-94e9-4969-84fc-37d49e63933b
author: minewiskan
ms.author: owend
ms.openlocfilehash: d64d1ac46e2571aa6f8065a8ea42e4cc43aa589e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661369"
---
# <a name="extending-olap-functionality"></a><span data-ttu-id="8af78-102">OLAP 기능 확장</span><span class="sxs-lookup"><span data-stu-id="8af78-102">Extending OLAP functionality</span></span>
  <span data-ttu-id="8af78-103">프로그래머는 여러 데이터베이스 애플리케이션에서의 사용 및 용도 변경 기능을 제공하는 어셈블리, 개인 설정 확장 프로그램 및 저장 프로시저를 작성하여 Analysis Services를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8af78-103">As a programmer, you can extend Analysis Services by writing assemblies, personalized extensions, and stored procedures that provide functionality you want to use and repurpose in multiple database applications.</span></span> <span data-ttu-id="8af78-104">어셈블리는 새 프로시저와 함수를 MDX 언어에 추가하거나 개인 설정 추가 기능을 사용하여 다차원 모델 기능을 확장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8af78-104">Assemblies are used to extend multidimensional models functionality by adding new procedures and functions to the MDX language or by means of the personalization addin.</span></span>  
  
 <span data-ttu-id="8af78-105">저장 프로시저를 사용하면 공통 코드를 한 번 개발하고 단일 위치에 저장할 수 있으므로 Analysis Services 데이터베이스 개발 및 구현을 간소화하여 외부 루틴을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8af78-105">Stored procedures can be used to call external routines, simplifying Analysis Services database development and implementation by allowing common code to be developed once and stored in a single location.</span></span> <span data-ttu-id="8af78-106">또한 MDX의 기본 기능에서 제공하지 않는 비즈니스 기능을 애플리케이션에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8af78-106">Stored procedures can be used to add business functionality to your applications that is not provided by the native functionality of MDX.</span></span>  
  
 <span data-ttu-id="8af78-107">개인 설정은 사용자마다 다른 동작을 제공하기 위해 큐브에 추가하는 사용자 지정 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8af78-107">Personalizations are custom objects that you add to a cube to provide a behavior that varies by user.</span></span> <span data-ttu-id="8af78-108">개인 설정은 큐브에서 영구 개체는 아니지만 사용자 세션 중 클라이언트 애플리케이션에서 동적으로 적용되는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8af78-108">Personalizations are not permanent objects in the cube, but are objects that the client application applies dynamically during the user's session.</span></span> <span data-ttu-id="8af78-109">예를 들어 데이터에 액세스하는 개인에 따라 통화 값의 통화를 변경하거나 개별화된 KPI를 제공하거나 온라인으로 구매하는 단골 고객에 대한 목표 제안 목록을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="8af78-109">Examples include changing the currency of a monetary value depending on the person accessing the data, providing individualized KPIs, or a targeted suggestion list for regular customers who purchase online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8af78-110">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="8af78-110">In This Section</span></span>  
 [<span data-ttu-id="8af78-111">개별화를 통해 OLAP 확장</span><span class="sxs-lookup"><span data-stu-id="8af78-111">Extending OLAP through personalizations</span></span>](extending-olap-through-personalizations.md)  
  
 [<span data-ttu-id="8af78-112">Analysis Services 개인 설정 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="8af78-112">Analysis Services Personalization Extensions</span></span>](analysis-services-personalization-extensions.md)  
  
 [<span data-ttu-id="8af78-113">저장 프로시저 정의</span><span class="sxs-lookup"><span data-stu-id="8af78-113">Defining Stored Procedures</span></span>](../../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
