---
title: '자습서: 데이터베이스 엔진 시작 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tutorials [connecting]
- tutorials [Database Engine]
- unable to connect [SQL Server]
- failure to connect [SQL Server]
- connecting tutorial [SQL Server]
ms.assetid: 655e709b-346b-469c-bddc-a5a0238d07e0
author: rothja
ms.author: jroth
ms.openlocfilehash: aaa1fb21c026d064c2b14db73aadc2b82e9c15d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660377"
---
# <a name="tutorial-getting-started-with-the-database-engine"></a><span data-ttu-id="37dc1-102">자습서: 데이터베이스 엔진 시작</span><span class="sxs-lookup"><span data-stu-id="37dc1-102">Tutorial: Getting Started with the Database Engine</span></span>
  <span data-ttu-id="37dc1-103">[!INCLUDE[ssDE](../includes/ssde-md.md)] 시작 자습서를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="37dc1-103">Welcome to the Getting Started with the [!INCLUDE[ssDE](../includes/ssde-md.md)] tutorial.</span></span> <span data-ttu-id="37dc1-104">이 자습서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 를 처음으로 사용하는 사용자 및 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]를 설치한 사용자를 위해 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="37dc1-104">This tutorial is intended for users who are new to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and who have installed [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or [!INCLUDE[ssExpress](../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="37dc1-105">이 간단한 자습서를 사용하면 [!INCLUDE[ssDE](../includes/ssde-md.md)]을 처음 사용하는 경우 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37dc1-105">This brief tutorial helps you get started using the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="37dc1-106">학습 내용</span><span class="sxs-lookup"><span data-stu-id="37dc1-106">What You Will Learn</span></span>  
 <span data-ttu-id="37dc1-107">이 자습서에서는 [!INCLUDE[ssDE](../includes/ssde-md.md)] 를 사용하여 로컬 컴퓨터와 다른 컴퓨터에서 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 에 연결하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="37dc1-107">This tutorial shows you how to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] on both the local computer and from another computer.</span></span>  
  
 <span data-ttu-id="37dc1-108">이 자습서는 다음 두 단원으로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37dc1-108">This tutorial is divided into two lessons:</span></span>  
  
 [<span data-ttu-id="37dc1-109">1단원: 데이터베이스 엔진에 연결</span><span class="sxs-lookup"><span data-stu-id="37dc1-109">Lesson 1: Connecting to the Database Engine</span></span>](lesson-1-connecting-to-the-database-engine.md)  
 <span data-ttu-id="37dc1-110">이 단원에서는 [!INCLUDE[ssDE](../includes/ssde-md.md)] 에 연결하는 방법과 추가 사용자가 연결할 수 있도록 설정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="37dc1-110">In this lesson, you will learn how to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] and enable additional people to connect.</span></span>  
  
 [<span data-ttu-id="37dc1-111">2단원: 다른 컴퓨터에서 연결</span><span class="sxs-lookup"><span data-stu-id="37dc1-111">Lesson 2: Connecting from Another Computer</span></span>](lesson-2-connecting-from-another-computer.md)  
 <span data-ttu-id="37dc1-112">이 단원에서는 프로토콜 설정, 포트 구성 및 방화벽 설정 구성을 포함하여 두 번째 컴퓨터에서 [!INCLUDE[ssDE](../includes/ssde-md.md)] 에 연결하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="37dc1-112">In this lesson, you will learn how to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] from a second computer, including enabling protocols, configuring ports, and configuring firewall settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37dc1-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="37dc1-113">Requirements</span></span>  
 <span data-ttu-id="37dc1-114">이 자습서에는 사전 지식이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37dc1-114">This tutorial has no knowledge prerequisites.</span></span>  
  
 <span data-ttu-id="37dc1-115">이 자습서를 사용하려면 시스템에 다음 항목이 설치되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37dc1-115">Your system must have the following installed to use this tutorial:</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]<span data-ttu-id="37dc1-116">입니다.</span><span class="sxs-lookup"><span data-stu-id="37dc1-116">.</span></span> [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] <span data-ttu-id="37dc1-117">는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 설치 프로그램으로 설치할 수도 있고 [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/?LinkId=144346)에서 다운로드하여 설치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37dc1-117">can be installed by running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] setup or by downloading and installing from [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=144346).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37dc1-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37dc1-118">See Also</span></span>  
 [<span data-ttu-id="37dc1-119">자습서: SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="37dc1-119">Tutorial: SQL Server Management Studio</span></span>](../ssms/tutorials/tutorial-sql-server-management-studio.md)  
  
  
