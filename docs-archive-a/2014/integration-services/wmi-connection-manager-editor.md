---
title: WMI 연결 관리자 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmiconnection.f1
helpviewer_keywords:
- WMI Connection Manager Editor
ms.assetid: 0ef2c913-0779-4a07-989e-3361cd83170b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e85cdd2157c8ebe4cb9e6b53f8c3b47ff102a7b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660020"
---
# <a name="wmi-connection-manager-editor"></a><span data-ttu-id="7e1d7-102">WMI 연결 관리자 편집기</span><span class="sxs-lookup"><span data-stu-id="7e1d7-102">WMI Connection Manager Editor</span></span>
  <span data-ttu-id="7e1d7-103">**WMI 연결 관리자** 대화 상자를 사용하여 서버에 대한 Microsoft WMI(Windows Management Instrumentation) 연결을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e1d7-103">Use the **WMI Connection Manager** dialog box to specify a Microsoft Windows Management Instrumentation (WMI) connection to a server.</span></span>  
  
 <span data-ttu-id="7e1d7-104">WMI 연결 관리자에 대한 자세한 내용은 [WMI Connection Manager](connection-manager/wmi-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7e1d7-104">To learn more about the WMI connection manager, see [WMI Connection Manager](connection-manager/wmi-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7e1d7-105">옵션</span><span class="sxs-lookup"><span data-stu-id="7e1d7-105">Options</span></span>  
 <span data-ttu-id="7e1d7-106">**이름**</span><span class="sxs-lookup"><span data-stu-id="7e1d7-106">**Name**</span></span>  
 <span data-ttu-id="7e1d7-107">연결 관리자의 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7e1d7-107">Provide a unique name for the connection manager.</span></span>  
  
 <span data-ttu-id="7e1d7-108">**설명**</span><span class="sxs-lookup"><span data-stu-id="7e1d7-108">**Description**</span></span>  
 <span data-ttu-id="7e1d7-109">연결 관리자에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7e1d7-109">Describe the connection manager.</span></span> <span data-ttu-id="7e1d7-110">설명에 해당 연결 관리자의 용도를 정의하면 패키지를 이해하기 쉬우며 유지 관리가 간편합니다.</span><span class="sxs-lookup"><span data-stu-id="7e1d7-110">As a best practice, describe the connection manager in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="7e1d7-111">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="7e1d7-111">**Server name**</span></span>  
 <span data-ttu-id="7e1d7-112">WMI 연결을 만들 서버의 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7e1d7-112">Provide the name of the server to which you want to make the WMI connection.</span></span>  
  
 <span data-ttu-id="7e1d7-113">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="7e1d7-113">**Namespace**</span></span>  
 <span data-ttu-id="7e1d7-114">WMI 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e1d7-114">Specify the WMI namespace.</span></span>  
  
 <span data-ttu-id="7e1d7-115">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="7e1d7-115">**Use Windows authentication**</span></span>  
 <span data-ttu-id="7e1d7-116">Windows 인증을 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7e1d7-116">Select to use Windows Authentication.</span></span> <span data-ttu-id="7e1d7-117">Windows 인증을 사용하면 연결할 때 사용자 이름 또는 암호를 제공할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e1d7-117">If you use Windows Authentication, you do not need to provide a user name or password for the connection.</span></span>  
  
 <span data-ttu-id="7e1d7-118">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="7e1d7-118">**User name**</span></span>  
 <span data-ttu-id="7e1d7-119">Windows 인증을 사용하지 않으면 연결할 때 사용자 이름을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e1d7-119">If you do not use Windows Authentication, you must provide a user name for the connection.</span></span>  
  
 <span data-ttu-id="7e1d7-120">**암호**</span><span class="sxs-lookup"><span data-stu-id="7e1d7-120">**Password**</span></span>  
 <span data-ttu-id="7e1d7-121">Windows 인증을 사용하지 않으면 연결할 때 암호를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e1d7-121">If you do not use Windows Authentication, you must provide the password for the connection.</span></span>  
  
 <span data-ttu-id="7e1d7-122">**Test**</span><span class="sxs-lookup"><span data-stu-id="7e1d7-122">**Test**</span></span>  
 <span data-ttu-id="7e1d7-123">연결 관리자 설정을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="7e1d7-123">Test the connection manager settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e1d7-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7e1d7-124">See Also</span></span>  
 <span data-ttu-id="7e1d7-125">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="7e1d7-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="7e1d7-126">[구성 관리용 WMI 공급자 개념](../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md) </span><span class="sxs-lookup"><span data-stu-id="7e1d7-126">[WMI Provider for Configuration Management Concepts](../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md) </span></span>  
 [<span data-ttu-id="7e1d7-127">서버 이벤트용 WMI 공급자 개념</span><span class="sxs-lookup"><span data-stu-id="7e1d7-127">WMI Provider for Server Events Concepts</span></span>](../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)  
  
  
