---
title: SMO 시작 하기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, about SQL Server Management Objects
- SMO [SQL Server], about SQL Server Management Objects
ms.assetid: ecc62702-c0d5-4180-b3c2-16ec5030caa7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4d90911932b5f9bfc91368e70e66d2b227a3964f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652763"
---
# <a name="getting-started-in-smo"></a><span data-ttu-id="631e6-102">SMO 시작</span><span class="sxs-lookup"><span data-stu-id="631e6-102">Getting Started in SMO</span></span>
  <span data-ttu-id="631e6-103">이 항목에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SMO (Management Objects) 사용을 시작 하는 방법에 대 한 정보가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e6-103">This topic contains information about getting started using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).</span></span> <span data-ttu-id="631e6-104">SMO 섹션은 개발자를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="631e6-104">The SMO section is aimed at developers.</span></span> <span data-ttu-id="631e6-105">다음 목록을 참조하면 SMO 개체 계층 구조, SMO에서 프로그램을 작성하기 위해 준비하는 방법, 여러 다른 언어로 SMO 프로그램을 작성하는 방법을 비롯하여 일반적인 프로그래밍 작업과 특정 프로그래밍 태스크에 대한 정보를 쉽게 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e6-105">The following list will help you to locate information about the SMO object hierarchy, how to prepare for writing programs in SMO, how to start writing an SMO program in different programming languages, and general and specific programming tasks.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="631e6-106">**SMO 준비**</span><span class="sxs-lookup"><span data-stu-id="631e6-106">**Preparing for SMO**</span></span><br /><br /> <span data-ttu-id="631e6-107">-   [SMO 준비](../../database-engine/dev-guide/preparing-to-use-smo.md) 에서는 시스템 요구 사항, 설치 및 sql-dmo와의 비교에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="631e6-107">-   [Preparing for SMO](../../database-engine/dev-guide/preparing-to-use-smo.md) provides information about system requirements, installation, and comparisons with SQL-DMO.</span></span><br /><br /> <span data-ttu-id="631e6-108">**개체 모델**</span><span class="sxs-lookup"><span data-stu-id="631e6-108">**Object Model**</span></span><br /><br /> <span data-ttu-id="631e6-109">- [개체 모델](smo-object-model.md) 은 SMO 개체 계층 구조와 개체가 서로 관련 되는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="631e6-109">-   The [Object Model](smo-object-model.md) describes the SMO object hierarchy and how the objects relate to one another.</span></span><br /><br /> <span data-ttu-id="631e6-110">**프로그래밍 언어**</span><span class="sxs-lookup"><span data-stu-id="631e6-110">**Programming Languages**</span></span><br /><br /> <span data-ttu-id="631e6-111">-   [프로그래밍 언어](smo-programming-languages.md) 는 프로그래밍 환경에 대해 설명 하 고, SMO 프로그램을 c #으로 작성 하기 시작 하 고 Visual Basic 하는 자세한 절차를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="631e6-111">-   [Programming Languages](smo-programming-languages.md) describes the programming environment and includes detailed procedures to start writing an SMO program in C# and Visual Basic.</span></span>|<span data-ttu-id="631e6-112">**SMO의 일반 프로그래밍**</span><span class="sxs-lookup"><span data-stu-id="631e6-112">**General Programming in SMO**</span></span><br /><br /> <span data-ttu-id="631e6-113">-   [Smo의 일반적인 프로그래밍](create-program/creating-smo-programs.md) 은 smo를 사용한 프로그래밍에 대 한 소개입니다.</span><span class="sxs-lookup"><span data-stu-id="631e6-113">-   [General Programming in SMO](create-program/creating-smo-programs.md) is an introduction to programming with SMO.</span></span> <span data-ttu-id="631e6-114">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결하는 방법과 속성, 메서드 및 컬렉션 사용 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="631e6-114">This topic describes how to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and how to use properties, methods, and collections.</span></span> <span data-ttu-id="631e6-115">추가적인 고급 항목에서는 데이터 형식, 트랜잭션, 캡처 모드 설정, 이벤트 및 예외 처리에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="631e6-115">More advanced topics describe data types, transactions, setting the capture mode, and event and exception handling.</span></span><br /><br /> <span data-ttu-id="631e6-116">**프로그래밍 관련 태스크**</span><span class="sxs-lookup"><span data-stu-id="631e6-116">**Programming Specific Tasks**</span></span><br /><br /> <span data-ttu-id="631e6-117">- [프로그래밍 특정 작업](tasks/programming-specific-tasks.md) 섹션에는 SMO를 사용 하 여 특정 태스크를 프로그래밍 하는 방법에 대 한 개념 및 절차가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e6-117">-   The [Programming Specific Tasks](tasks/programming-specific-tasks.md) section contains concepts and procedures about how to program specific tasks by using SMO.</span></span> <span data-ttu-id="631e6-118">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 완전한 프로그래밍 방식 관리에 대해서도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="631e6-118">The topic also describes complete programmatic management of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
  
