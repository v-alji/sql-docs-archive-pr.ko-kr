---
title: FILESTREAM 액세스를 위한 방화벽 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- Windows Firewall [Database Engine], FILESTREAM
- FILESTREAM [SQL Server], Windows Firewall
ms.assetid: fc52007f-c26f-4f8e-b9d8-55a7978f4d56
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8b787403fefdd336dd82bf7ccb93cdf21fe5a90d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659491"
---
# <a name="configure-a-firewall-for-filestream-access"></a><span data-ttu-id="19fa0-102">FILESTREAM 액세스를 위한 방화벽 구성</span><span class="sxs-lookup"><span data-stu-id="19fa0-102">Configure a Firewall for FILESTREAM Access</span></span>
  <span data-ttu-id="19fa0-103">방화벽으로 보호되는 환경에서 FILESTREAM을 사용하려면 클라이언트와 서버에서 DNS 이름을 FILESTREAM 파일이 포함된 서버로 확인할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19fa0-103">To use FILESTREAM in a firewall-protected environment, both the client and server must be able to resolve DNS names to the server that contains the FILESTREAM files.</span></span> <span data-ttu-id="19fa0-104">FILESTREAM을 사용하려면 Windows 파일 공유 포트 139 및 445가 열려 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19fa0-104">FILESTREAM requires the Windows file-sharing ports 139 and 445 to be open.</span></span>  
  
### <a name="to-open-the-windows-file-sharing-ports-on-a-computer-that-is-running-windows-7"></a><span data-ttu-id="19fa0-105">Windows 7을 실행하는 컴퓨터에서 Windows 파일 공유 포트를 열려면</span><span class="sxs-lookup"><span data-stu-id="19fa0-105">To open the Windows file-sharing ports on a computer that is running Windows 7</span></span>  
  
1.  <span data-ttu-id="19fa0-106">제어판에서 **Windows 방화벽**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="19fa0-106">In Control Panel, open **Windows Firewall**.</span></span>  
  
2.  <span data-ttu-id="19fa0-107">왼쪽 창에서 **고급 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19fa0-107">In the left pane, click **Advanced settings**.</span></span> <span data-ttu-id="19fa0-108">관리자 암호를 입력하거나 확인하라는 메시지가 표시되면 암호를 입력하거나 확인을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="19fa0-108">If you're prompted for an administrator password or confirmation, type the password or provide confirmation.</span></span>  
  
3.  <span data-ttu-id="19fa0-109">**고급 보안이 포함된 Windows 방화벽** 대화 상자의 왼쪽 창에서 **인바운드 규칙**을 클릭한 다음 오른쪽 창에서 **새 규칙**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19fa0-109">In the **Windows Firewall with Advanced Security** dialog box, in the left pane, click **Inbound Rules**, and then, in the right pane, click **New Rule**.</span></span>  
  
4.  <span data-ttu-id="19fa0-110">새 인바운드 규칙 마법사의 지시에 따라 TCP 포트 139를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="19fa0-110">Follow the instructions in the New Inbound Rule wizard to add TCP port 139.</span></span>  
  
5.  <span data-ttu-id="19fa0-111">이전 단계를 반복하여 TCP 포트 445를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="19fa0-111">Repeat the previous step to add TCP port 445.</span></span>  
  
6.  <span data-ttu-id="19fa0-112">**고급 보안이 포함된 Windows 방화벽** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="19fa0-112">Close the **Windows Firewall with Advanced Security** dialog box.</span></span>  
  
  
