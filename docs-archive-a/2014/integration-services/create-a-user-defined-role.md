---
title: 사용자 정의 역할 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c4128993-2333-48c7-84b1-e51cdcea393d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a0ee905c2636e20315c2180a6be8f8e40f76d5f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649609"
---
# <a name="create-a-user-defined-role"></a><span data-ttu-id="4a930-102">사용자 정의 역할 만들기</span><span class="sxs-lookup"><span data-stu-id="4a930-102">Create a User-Defined Role</span></span>
    
### <a name="to-create-a-user-defined-role"></a><span data-ttu-id="4a930-103">사용자 정의 역할을 만들려면</span><span class="sxs-lookup"><span data-stu-id="4a930-103">To create a user-defined role</span></span>  
  
1.  <span data-ttu-id="4a930-104">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4a930-104">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="4a930-105">**보기** 메뉴에서 **개체 탐색기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4a930-105">Click **Object Explorer** on the **View** menu.</span></span>  
  
3.  <span data-ttu-id="4a930-106">개체 탐색기 도구 모음에서 **연결**, **데이터베이스 엔진**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4a930-106">On the Object Explorer toolbar, click **Connect**, and then click **Database Engine**.</span></span>  
  
4.  <span data-ttu-id="4a930-107">**서버에 연결** 대화 상자에 서버 이름을 입력하고 인증 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a930-107">In the **Connect to Server** dialog box, provide a server name and select an authentication mode.</span></span> <span data-ttu-id="4a930-108">마침표(.), (local) 또는 `localhost`을 사용하여 로컬 서버를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a930-108">You can use a period (.), (local), or `localhost` to indicate the local server.</span></span>  
  
5.  <span data-ttu-id="4a930-109">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4a930-109">Click **Connect**.</span></span>  
  
6.  <span data-ttu-id="4a930-110">데이터베이스, 시스템 데이터베이스, msdb, 보안 및 역할을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4a930-110">Expand Databases, System Databases, msdb, Security, and Roles.</span></span>  
  
7.  <span data-ttu-id="4a930-111">역할 노드에서 데이터베이스 역할을 마우스 오른쪽 단추로 클릭하고 **새 데이터베이스 역할**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4a930-111">In the Roles node, right-click Database Roles, and click **New Database Role**.</span></span>  
  
8.  <span data-ttu-id="4a930-112">일반 페이지에 이름을 입력하고 필요에 따라 소유자 및 소유한 스키마를 지정한 다음 역할 멤버를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4a930-112">On the General page, provide a name and optionally, specify an owner and owned schemas and add role members.</span></span>  
  
9. <span data-ttu-id="4a930-113">필요에 따라 **권한** 을 클릭하고 개체 사용 권한을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4a930-113">Optionally, click **Permissions** and configure object permissions.</span></span>  
  
10. <span data-ttu-id="4a930-114">필요에 따라 **확장 속성** 을 클릭하고 확장 속성을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4a930-114">Optionally, click **Extended Properties** and configure any extended properties.</span></span>  
  
11. <span data-ttu-id="4a930-115">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4a930-115">Click **OK**.</span></span>  
  
  
