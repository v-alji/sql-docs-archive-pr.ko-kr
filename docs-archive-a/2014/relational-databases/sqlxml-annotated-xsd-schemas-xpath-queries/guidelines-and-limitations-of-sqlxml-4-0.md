---
title: SQLXML 4.0의 지침 및 제한 사항 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, about SQLXML
ms.assetid: fe433d30-90a1-421e-85c6-af13294dc18d
author: rothja
ms.author: jroth
ms.openlocfilehash: e020cbf0ac32e4c878b0b74b67e7c9c679d5d178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638623"
---
# <a name="guidelines-and-limitations-of-sqlxml-40"></a><span data-ttu-id="7234e-102">SQLXML 4.0에 대한 지침 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="7234e-102">Guidelines and Limitations of SQLXML 4.0</span></span>
  <span data-ttu-id="7234e-103">SQLXML 4.0에서 작업을 수행할 때는 다음 사항을 기억해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7234e-103">Remember the following when working with SQLXML 4.0:</span></span>  
  
-   <span data-ttu-id="7234e-104">쿼리 결과로 반환되는 XML은 XML을 생성한 매핑 스키마에 대해 유효성이 검사되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7234e-104">XML returned as a query result is not validated against the mapping schema that generated the XML.</span></span>  
  
-   <span data-ttu-id="7234e-105">SQLXML 4.0에는 버전 독립 및 버전 종속 PROGID가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7234e-105">SQLXML 4.0 includes version-independent and version-dependent PROGIDs.</span></span> <span data-ttu-id="7234e-106">모든 프로덕션 애플리케이션에는 버전 종속 PROGID를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7234e-106">It is recommended that all production applications use version-dependent PROGIDs.</span></span> <span data-ttu-id="7234e-107">특히 SQLXML 4.0은 이전 버전과 완벽하게 호환되지 않는다는 점을 감안할 때 이는 매우 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="7234e-107">This is especially important because SQLXML 4.0 is not fully backward compatible.</span></span> <span data-ttu-id="7234e-108">버전 종속 PROGID를 사용하면 새 버전을 설치할 때 발생할 수 있는 프로덕션 오류를 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7234e-108">Using version dependent PROGIDs protects from possible production failures when you install newer releases.</span></span> <span data-ttu-id="7234e-109">버전이 업데이트되면서 버그 픽스, 디자인 변경 등의 다양한 이유로 프로그램 동작이 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7234e-109">From release to release, program behavior may change for a variety of reasons, such as bug fixes, possible design changes, and so on.</span></span> <span data-ttu-id="7234e-110">버전 종속 PROGID를 사용하면 새 버전을 설치할 때 발생할 수 있는 예기치 않은 오류를 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7234e-110">Using version-dependent PROGIDs protects from unexpected failure when you install newer releases.</span></span> <span data-ttu-id="7234e-111">새 버전을 설치할 때 버전 종속 PROGID를 사용하면 이후에도 애플리케이션이 오류 없이 정상적으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="7234e-111">With version-dependent PROGIDs, when you install a newer release, your application will continue to work without failure.</span></span> <span data-ttu-id="7234e-112">이전 버전 종속 PROGID를 변경하고 새 버전의 최신 버전 종속 PROGID를 사용하려면 프로덕션 환경에 설치하기 전에 애플리케이션을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7234e-112">If you decide to change the previous version-dependent PROGIDs and use the recent version-dependent PROGIDs in a newer release, you must test your application before putting it into production.</span></span> <span data-ttu-id="7234e-113">예를 들어 다음과 같은 시나리오에서 버전 독립 PROGID를 사용하는 애플리케이션에 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7234e-113">For example, applications using version-independent PROGIDs may fail in the following scenario:</span></span>  
  
     <span data-ttu-id="7234e-114">SQLXML 4.0 및 버전 독립 PROGID를 사용하는 애플리케이션을 실행하고 있는데 다른 몇 가지 소프트웨어 프로그램을 설치하려는 경우.</span><span class="sxs-lookup"><span data-stu-id="7234e-114">You are running an application that uses SQLXML 4.0 and version-independent PROGIDs, and you decide to install some other software program.</span></span> <span data-ttu-id="7234e-115">해당 프로그램에 의해 이전 버전의 SQLXML이 설치될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7234e-115">This program might install an earlier version of SQLXML.</span></span> <span data-ttu-id="7234e-116">해당 애플리케이션의 버전 독립 PROGID가 애플리케이션에 현재 사용되고 있는 기능이 없을 수도 있는 이전 버전의 SQLXML을 가리키게 되므로 애플리케이션에 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7234e-116">Your application may fail because the version-independent PROGIDS in your application now point to the earlier version of SQLXML, which may or may not have the SQLXML feature that your application is using.</span></span>  
  
-   <span data-ttu-id="7234e-117">어떤 이유로 든 SQLXMLOLEDB 공급자를 사용 하지 않고 SQLXML 기능에 대해 SQLOLEDB 공급자를 사용 하려면 **Sqlxml 버전** 속성을 "sqlxml. 4.0"으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7234e-117">If for any reason you don't want to use the SQLXMLOLEDB provider, and instead want to use the SQLOLEDB provider for SQLXML features, set the **SQLXML Version** property to "SQLXML.4.0".</span></span>  
  
  
