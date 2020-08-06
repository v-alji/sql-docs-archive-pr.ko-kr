---
title: 서버 찾아보기(네트워크 서버) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.browseservers.network.f1
ms.assetid: a59ffcd6-4b69-4c5c-9740-699ccb2183fb
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0ba5e4e5dd6d9a6541a98e0cb30229d7335bac24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652369"
---
# <a name="browse-for-servers-network-servers"></a><span data-ttu-id="6c412-102">서버 찾아보기(네트워크 서버)</span><span class="sxs-lookup"><span data-stu-id="6c412-102">Browse for Servers (Network Servers)</span></span>
  <span data-ttu-id="6c412-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 요소에 연결 시 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스의 정확한 이름을 모르는 경우 **서버 이름** 상자에서 **더 찾아보기**를 클릭하여 **서버 찾아보기** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6c412-103">If you are connecting to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] component and you do not know the exact name of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance, click **Browse for more** in the **Server name** box to open the **Browse for Servers** dialog box.</span></span>  
  
 <span data-ttu-id="6c412-104">이 대화 상자는 서버 컴퓨터에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser 서비스로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="6c412-104">This dialog is populated by the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser service on the server computers.</span></span> <span data-ttu-id="6c412-105">인스턴스의 이름이 목록에 나타나지 않는 경우 다음과 같은 여러 가지 이유 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c412-105">There are several reasons why the name of an instance might not appear in the list:</span></span>  
  
-   <span data-ttu-id="6c412-106">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser 서비스가 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 실행하는 컴퓨터에서 실행 중이지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c412-106">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser service might not be running on the computer running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="6c412-107">UDP 포트 1434가 방화벽에 의해 차단되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c412-107">UDP port 1434 might be blocked by a firewall.</span></span>  
  
-   <span data-ttu-id="6c412-108">**인스턴스 숨기기** 플래그가 설정되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c412-108">The **HideInstance** flag might be set.</span></span>  
  
 <span data-ttu-id="6c412-109">목록에 나타나지 않는 인스턴스에 연결하려면 TCP/IP 포트 번호 또는 명명된 파이프 이름을 포함하여 인스턴스의 전체 연결 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6c412-109">To connect to an instance that does not appear in the list, type a full connection string for the instance, including the TCP/IP port number or the named pipes pipe name.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6c412-110">옵션</span><span class="sxs-lookup"><span data-stu-id="6c412-110">Options</span></span>  
 <span data-ttu-id="6c412-111">**네트워크에서 연결할 SQL Server 인스턴스를 선택하십시오.**</span><span class="sxs-lookup"><span data-stu-id="6c412-111">**Select a SQL Server instance in the network for your connection**</span></span>  
 <span data-ttu-id="6c412-112">트리에 표시된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스를 클릭하여 연결할 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c412-112">Designate the server you want to connect to by clicking on the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance displayed in the tree.</span></span> <span data-ttu-id="6c412-113">또는 기호로 표시 된 노드를 클릭 하 여 트리 뷰의 일부를 표시 하거나 숨길 수 있습니다 **+** **-** .</span><span class="sxs-lookup"><span data-stu-id="6c412-113">You can show or hide portions of the tree view by clicking on the nodes marked with a **+** or **-** symbol.</span></span>  
  
  
